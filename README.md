# The prime number theorem via largest-prime deletion

Jeffery Kline

[![Version DOI: 10.5281/zenodo.23038366](https://zenodo.org/badge/DOI/10.5281/zenodo.23038366.svg)](https://doi.org/10.5281/zenodo.23038366)

**Version 0.1.0 — admitted, released 2026-09-29.** The immutable release is
[`v0.1.0`](https://github.com/jeff-kline/largest-prime-deletion/releases/tag/v0.1.0),
archived at version DOI [`10.5281/zenodo.23038366`](https://doi.org/10.5281/zenodo.23038366). The concept DOI
[`10.5281/zenodo.23038365`](https://doi.org/10.5281/zenodo.23038365) resolves to the latest version; cite the
version DOI for reproducibility. Admission under the project's
[public research standard](https://jeff-kline.github.io/posts/research-program/index.html)
is a release decision, not peer review or a correctness certificate. The
tagged snapshot retains its prepublication "release candidate" wording because
the DOI did not exist when it was made.

The paper is [paper/main.pdf](paper/main.pdf); its source is
[paper/main.tex](paper/main.tex).

## Introduction

This paper proves the prime number theorem in its equivalent form

`M(n) = μ(1) + ⋯ + μ(n) = o(n)`

by comparing successive deletions of largest prime factors. Here μ is the
Möbius function: zero on integers divisible by a prime square, and otherwise
+1 or −1 according as the number of prime factors is even or odd, with μ(1) = 1.

Choose an integer uniformly among the squarefree positive integers at most n.
Delete its K largest prime factors, stopping at 1, and let `ν_{n,K}` be the
distribution of the integer that remains. For example, successive deletions
take 210 to 30, 6, 2, and then 1. The paper proves

`limsup_{n→∞} TV(ν_{n,K}, ν_{n,K+1}) = O((log K)^(−1/4))` as K → ∞.

Total variation distance is the largest difference between the probabilities
the two distributions assign to any set. The bound therefore controls every
bounded function of the remaining integer. Since μ changes sign with each
deletion until the integer reaches 1, the bound forces Möbius cancellation
and hence the prime number theorem. The paper proves the cancellation
statement and takes the classical equivalence as known.

The proof develops the multiplier-comparison method of Richter and
Bergelson–Richter. Its main estimate matches products of d and d + 1 primes
of nearly equal size, using prime windows that move with n. The factors are
large enough to be deleted: the extra factor accounts for the extra deletion,
leaving the same number of deletions to perform on the cofactor. The matching
estimate has constants independent of the logarithmic width of the window.

The argument uses elementary prime estimates and Plancherel's theorem,
without assuming the prime number theorem. The limit in n is taken first,
with K fixed, so the depth bound gives no rate for `M(n)/n` and no new
prime-counting error term. The use of Plancherel means this is not an
elementary proof in the strict sense.

## Contribution and prior work

The proposed contribution is the uniform matching estimate for products of
adjacent degrees and its use to prove the deletion theorem without assuming
the prime number theorem. The multiplier-averaging principle, squarefree
sampling, the parity argument, and the Fourier identities have established
precedents, credited in Section 1.1 of the paper.

The statement of the deletion theorem alone is not claimed as new, and its
rate is not claimed to be sharp. A derivation using known prime number theorem
estimates, and an alternative moving-window adaptation of Richter's method,
remain unresolved comparisons. The targeted literature review found no exact
counterpart to the deletion theorem or the uniform matching estimate in the
sources compared; it does not establish global priority. See Section 1.1 and
[audit/reports/prior-art-audit.md](audit/reports/prior-art-audit.md).

## Evidence and limits

- The theorem and its corollary are proved in the paper from elementary
  counting, elementary prime estimates proved there, and Plancherel's theorem.
  No numerical computation is used as evidence.
- The proof was checked by process-separated AI audits (see `audit/`). No
  independent human expert has reviewed it. Agreement among AI checks is
  evidence about a process, not independent validation.
- All constants in the depth bound are absolute, but the threshold in n
  depends on the fixed parameters. No simultaneous estimate in n and K is
  claimed.

## Reproduce

Requirements: pdfLaTeX (tested with TeX Live 2021) and Poppler's `pdfinfo` and
`pdftotext`. No Python is needed.

```sh
make paper                        # three pdfLaTeX passes; fixed SOURCE_DATE_EPOCH
make check                        # TeX log, page count, unresolved references
shasum -a 256 -c MANIFEST.sha256
```

`make check` checks the document's consistency; it does not check proofs.

## Repository contents

- `paper/`: LaTeX source `main.tex` and reading copy `main.pdf`.
- `audit/`: proof and prior-art audit reports and the ledger of findings and
  dispositions.
- `ADMISSION.md`, `VERIFICATION.md`, `CORRECTIONS.md`, `CITATION.cff`,
  `MANIFEST.sha256`: release records.

## Role of AI

AI did the derivations, literature search, exposition, and audits under the
author's direction. The author chose the question and is responsible for the
result and its corrections.

## License

GPL-3.0-only. See [LICENSE](LICENSE).
