# Total variation under largest-prime deletion

Jeffery Kline

**Version 0.1.0 — release candidate.** No tag, archive, or DOI exists yet;
there is no stable citation for this version. Status is tracked in
[ADMISSION.md](ADMISSION.md) under the project's
[public research standard](https://jeff-kline.github.io/posts/research-program/index.html).

The paper is [paper/main.pdf](paper/main.pdf); its source is
[paper/main.tex](paper/main.tex).

## Introduction

Choose an integer uniformly among the squarefree positive integers at most n
(those not divisible by the square of any prime, including 1). Delete its K
largest prime factors, stopping at 1, and let `ν_{n,K}` be the distribution of
the integer that remains. For example, deleting largest primes one at a time
takes 210 to 30, 6, 2, and then 1.

The paper proves that consecutive depths give nearly the same distribution
once K is large:

```text
limsup_{n→∞} TV(ν_{n,K}, ν_{n,K+1}) = O((log K)^(−1/4))   as K → ∞.
```

Here TV is total variation distance, the largest difference between the
probabilities the two laws assign to any one set of integers, so the bound
controls every bounded test of the remaining integer at once. The limit in n
is taken first, with K fixed.

The proof develops the multiplier-comparison method of Richter and of
Bergelson and Richter: bias the random integer toward multiples of a random
multiplier b, and compare two such biases. Here the multipliers are products of
d or d + 1 primes from a window n^c < p ≤ n^β that moves with n, each prime
drawn with probability proportional to 1/p. A weighted Fourier estimate
couples the two products so that their actual logarithms nearly agree, with
constants that do not depend on the logarithmic width log(β/c) of the window. A greatest-common-divisor
bound and an exact deletion identity carry this coupling over to the remaining
integers. Testing against the Möbius function (μ(m) = 0 if m is not squarefree, and
otherwise +1 or −1 as m has an even or odd number of prime factors), whose sign
flips with each deletion, then gives

```text
M(n) = μ(1) + μ(2) + ... + μ(n) = o(n),
```

which is classically equivalent to the prime number theorem. The argument uses
elementary prime estimates and Plancherel's theorem; it does not assume the
prime number theorem.

**Limits.** Because the limit in n is taken first, the depth bound gives no
rate for `M(n)/n` and no new error term for the Mertens function or prime
counting. The proof is not elementary in the strict sense: Plancherel's theorem
is used explicitly.

## What is new, and what is not

The paper puts forward two things: the deletion theorem above, for the full
distribution of the remaining integer, proved without assuming the prime
number theorem; and the uniform matching estimate for products of adjacent
degrees (Proposition 6.3, built on Lemmas 5.1 and 6.2). `M(n) = o(n)` is a
consequence, not the headline.

The statement of the deletion theorem by itself is not claimed as new. Since
the prime number theorem is known, standard asymptotics for integers with a
prescribed number of large prime factors may already determine the limit in n,
possibly with a better rate in K. That comparison has not been carried out, and
the rate `(log K)^(−1/4)` is not claimed to be sharp.

Established methods used here, and credited in Section 1.1 of the paper:

- **Richter (2021)** and **Bergelson–Richter (2022)**: comparing divisor
  averages over matched multiplier sets, controlled by a reciprocal-weighted
  greatest-common-divisor average, a principle they trace to Daboussi and
  Kátai. Bergelson–Richter also treat squarefree sampling; their proof of the
  matched-set lemma uses the prime number theorem, so those sets are not
  available here.
- **Li, Wang, Wang, and Yi (2025)**: shift invariance for bounded functions of
  the number of prime factors over squarefree integers. That controls the
  prime-factor count, not the remaining integer itself.
- **Arratia (2002)**: couplings of prime factorizations with independent and
  Poisson–Dirichlet models; a different conclusion, and the fine coupling there
  uses a prime number theorem error estimate.
- **Nourdin–Poly (2015)**: total-variation smoothing for normalized sums of a
  fixed law; the summand law here changes with n.
- **McNamara (2021)** and **Koukoulopoulos (2013)**: other dynamical and
  Fourier-analytic routes to the prime number theorem. Neither a dynamical
  reading nor the use of Fourier analysis is claimed as new.
- **Standard tools**: reading `M(n)` off the sign change of μ under one more
  deletion, the elementary prime estimates, Plancherel's theorem, and the
  fractional-seminorm identity in Lemma 6.2 are not claimed as new.

A fixed multiplier does not simply disappear under deletion: Remark 2.5 shows
that it typically survives any fixed number of deletions. The moving lower
bound on multiplier primes is what makes the transfer work.

These comparisons come from a bounded, targeted reading of the cited sources.
No exact counterpart to the deletion theorem or to the uniform matching
estimate was found in them. That is not a claim of worldwide priority. A
moving-window variant of Richter's construction might give the qualitative
limit without Fourier analysis; it has not been checked, and it is not expected
to give the rate or the uniform matching estimate. The details and
unread sources are in [audit/](audit/).

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
