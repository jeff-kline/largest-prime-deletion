# Verification record — version 0.1.0 (release candidate)

Recorded 2026-09-28.

## What is verified here

This record covers artifact consistency and reproducibility. The document
builds deterministically from a clean checkout, its TeX log is clean, and every
tracked file matches the manifest. It does not verify proofs. The proof audits,
source comparisons, and their dispositions are in `audit/LEDGER.md` and
`audit/reports/`.

No theorem in the paper rests on a numerical computation. The isolated
failure search ran small numerical probes of two intermediate statements, and
the proof audit numerically confirmed a Fourier constant. Both are recorded in
their reports. They are not release evidence and are not reproduced here.

## Environment

| Tool | Version |
|---|---|
| pdfTeX | 3.141592653-2.6-1.40.22 (TeX Live 2021, MacPorts 2021.58693_2) |
| Poppler `pdfinfo` / `pdftotext` | 26.07.0 |
| GNU Make | 3.81 |
| OS | macOS 26.6.2 (Darwin 25.6.0) |

The paper uses the TeX installation's default fonts. The Makefile fixes
`SOURCE_DATE_EPOCH=1790553600` (2026-09-28 00:00 UTC) and `FORCE_SOURCE_DATE=1`,
so the PDF creation date and identifiers are fixed. No Python is used to build
or check the release.

## Commands and outputs

```sh
make paper    # three pdfLaTeX passes
make check
shasum -a 256 paper/main.pdf
shasum -a 256 -c MANIFEST.sha256
```

`make check` output:

```text
Title:           Total variation under largest-prime deletion
Subject:         Version 0.1.0, release candidate
Author:          Jeffery Kline
Pages:           14
check: PASS (document consistency only; not a proof check)
```

`make check` fails on TeX warnings, overfull or underfull boxes, undefined
references, rerun requests, a page count other than 14, or unresolved `??` in
the PDF text.

## Reproduction evidence

- **Clean checkout.** `git archive` of the candidate commit was extracted into
  an empty scratch directory with no auxiliary files. `make paper` and
  `make check` succeeded there, and the rebuilt `paper/main.pdf` was
  byte-identical to the tracked copy. The SHA-256 is recorded in
  `ADMISSION.md`.
- **Repeat build.** Two consecutive warm builds in the working tree produced
  identical bytes.
- **Rendering.** All 14 pages of the candidate PDF were rendered and inspected
  for layout. Pages 1–3 and 14 (title block, abstract, related work,
  bibliography) were read at reading resolution; pages 4–13 were checked at
  contact-sheet resolution. The title block is centred and no display is
  clipped. Line-level overflow is covered by `make check`.
