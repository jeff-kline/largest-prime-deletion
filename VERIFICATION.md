# Verification record — version 0.1.0 (release candidate)

Initial candidate recorded 2026-09-28; prose revision checked 2026-09-29.

## What is verified here

This record covers artifact consistency and reproducibility. The current revised source builds deterministically from empty auxiliary state,
its TeX log is clean, and every manifest entry matches. The earlier candidate
also passed a clean committed-archive rebuild; that check must be repeated
after the revised tree is committed. It does not verify proofs. The proof audits,
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
Title:           The prime number theorem via largest-prime deletion
Subject:         Version 0.1.0, release candidate
Author:          Jeffery Kline
Pages:           14
check: PASS (document consistency only; not a proof check)
```

`make check` fails on TeX warnings, overfull or underfull boxes, undefined
references, rerun requests, a page count other than 14, or unresolved `??` in
the PDF text.

## Earlier candidate reproduction evidence (2026-09-28)

- **Clean checkout.** `git archive` of the candidate commit was extracted into
  an empty scratch directory with no auxiliary files. `make paper` and
  `make check` succeeded there, and the rebuilt `paper/main.pdf` was
  byte-identical to the tracked copy. The earlier PDF SHA-256 was
  `2dd08930f32d66cf575c0db9a19baf89f179318164b997819c95692198d1c562`.
- **Repeat build.** Two consecutive warm builds in the working tree produced
  identical bytes.
- **Rendering.** All 14 pages of the candidate PDF were rendered and inspected
  for layout. Pages 1–3 and 14 (title block, abstract, related work,
  bibliography) were read at reading resolution; pages 4–13 were checked at
  contact-sheet resolution. The title block is centred and no display is
  clipped. Line-level overflow is covered by `make check`.

## Prose revision checks (2026-09-29)

The abstract and README now lead with the prime number theorem in its Möbius
form. The introduction explains the extra-factor/extra-deletion comparison.
Proof bodies, equations, and theorem assertions are unchanged; this editorial
review is not a fresh proof audit.

- The revised source was built twice with no auxiliary files; both builds
  produced identical PDF bytes.
- `make check` passed: 14 pages, no TeX warnings or bad boxes, no unresolved
  references. All 14 rendered pages were inspected for layout.
- Revised PDF SHA-256 (committed at `f75f465`): `19d9e2f0a9ea82a0619d1dc0165199290f9c814f736b87002909404b3f4bd72a`; a clean `git archive` rebuild of `f75f465` reproduced it.
- Title changed 2026-09-29 to "The prime number theorem via largest-prime deletion"; rebuilt twice with identical bytes, `make check` PASS, title block inspected. PDF SHA-256: `bb59bd84ba633980aad5c1df93d233ebca0cd5529a6309fb6912e0c3c1495e1f`.
- The manifest was regenerated and checked after the prose and record edits.
- Refreeze (2026-09-29): `git archive b78722d` was extracted into an empty
  scratch directory. `make paper` and `make check` succeeded, and the rebuilt
  PDF was byte-identical (`bb59bd84ba633980aad5c1df93d233ebca0cd5529a6309fb6912e0c3c1495e1f`). The refreeze commit changes records only.
