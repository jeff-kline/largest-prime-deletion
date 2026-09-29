# Novelty and positioning assessment

Date: September 28, 2026. Scope: targeted primary-source comparison for the consolidated draft. This is an internal, nonindependent assessment, not an external referee report. No new agents or numerical experiments were used.

## Result

Position the paper as **Total variation under largest-prime deletion**. Lead with the law of the remaining integer and its `O((log K)^(-1/4))` adjacent-depth bound. Present the uniform product-matching estimate as the technical contribution and `M(n)=o(n)` as a consequence. The focused search did not locate the exact deletion theorem or an estimate supplying the same moving-window matching with the needed parameter uniformity. This supports a specific provisional novelty case, not an exhaustive priority verdict.

Do not claim novelty for squarefree sampling, reciprocal multiplier weighting, gcd-based divisor averaging, parity testing, elementary positive-prime estimates, Plancherel, or the fractional seminorm identity.

## Source comparison locations

The manuscript's Section 1.1 contains the substantive comparisons and bibliography. Primary texts checked:

- [Richter, corrected v3](https://arxiv.org/pdf/2002.03255v3): Theorem 1.1, Propositions 2.1–2.2, Lemma 3.3, and the construction in Section 3, including the correction to (3.12).
- [Bergelson–Richter, v3](https://arxiv.org/pdf/2002.03498v3): Corollary 1.8, Proposition 2.1, Lemmas 2.2–2.3 and the associated transfer argument.
- [Li–Wang–Wang–Yi, v2](https://arxiv.org/pdf/2405.18157v2): Theorems 1.1, 1.2 and 1.7. The squarefree count-shift theorem is explicit prior art; restrictions on the largest prime factor also occur.
- [Arratia](https://arxiv.org/pdf/1305.0941): Sections 3.4–3.5, the statements of Theorems 3 and 5, and the PNT-dependent estimate (34).
- [Nourdin–Poly](https://arxiv.org/pdf/1310.4266): Theorem 1.2, hypotheses for their invariance principle, and the distinction between fixed-law CLT smoothing and the varying densities used here.
- [McNamara](https://arxiv.org/pdf/2002.04007): Selberg-symmetry input and the prime/semiprime comparison; publication metadata checked on the [journal page](https://hrj.episciences.org/8924).
- [Koukoulopoulos](https://dms.umontreal.ca/~koukoulo/documents/publications/pnt.pdf): introductory statement of the Fourier/elementary approach and its relationship to multiplicative-function methods.

These are targeted section checks, not complete audits of every cited paper. Daboussi's original paper was not obtained and is not represented as directly inspected. General convolution-limit literature was sampled, not exhausted.

## Tests of an immediate derivation

### 1. Push forward to a prime-factor count

This loses information. A bound on the count distributions does not in general control total variation on the remaining integers. For example, point masses at 2 and 3 have identical prime-factor counts and total variation one. This elementary example is an obstruction to that inference, not a counterexample to any cited theorem. Our theorem is uniform over bounded tests of the remaining integer, which can vary with n.

### 2. Substitute fixed multiplier sets

This fails at the exact deletion identity. For any fixed squarefree b>1 and fixed K, a typical eligible cofactor a has at least K prime factors above P+(b). Consequently `T^K(ab)=b T^K(a)` with probability tending to one: b survives. The new manuscript Remark 2.5 proves this directly from the existing bounded-prime-count lemma. Our construction instead forces every multiplier factor above `n^(1/(K+1))`, and bounds the multiplier by `n^(1/8)`, so the factor is necessarily deleted. This is a real distinction in the needed hypotheses, not a proof that no adaptation of earlier constructions exists.

### 3. Move the earlier finite construction with n

A bare finite-set existence theorem gives no simultaneous control of minimum factor, maximum product, size matching, and sampling error relative to n. Establishing all four together is the extra obligation. In particular, the logarithmic-index progression construction cannot just be placed unchanged in a fixed exponent window: if its progression step is s comparable to log n, then its harmonic mass within [s, C s] is O_C(1/s), rather than a fixed positive amount. This diagnoses the literal rescaling shortcut; a different selection or weighting could still repair it.

No complete short adaptation was found. It remains a plausible future comparison and should not be described as impossible.

### 4. Replace the smoothing lemma by a standard limit theorem

The precise requirement is an iterated limit for f_n^{*h}, with n-dependent density, jitter a/log n, an upper envelope J/(Hx), and an L1 bound whose constant is independent of H. Then h increases while H must substantially exceed h squared. A result about normalized sums of one fixed distribution does not by itself establish this uniformity. An unweighted L2-to-L1 conversion in our setting incurs a factor comparable to exp(H/2); the weighted argument avoids it. The standard Fourier identity is not the novelty candidate; the envelope-dependent bound and simultaneous parameter regime are.

### 5. Use existing prime-factor couplings

A bound on expected logarithmic displacement does not imply equality of integer-valued outcomes with high probability, or total variation closeness of the residual integers. Additionally, a PNT-dependent fine coupling cannot replace our matching step in an independent proof of M=o(n). This separates the target and the allowed inputs; it does not exclude a PNT-dependent alternative proof of the deletion theorem.

## Claim ledger

| Item | Position |
|---|---|
| Reciprocal-weighted gcd averaging | Established method; attributed explicitly |
| Squarefree restriction and count-shift cancellation | Established; not a novelty claim |
| Full adjacent-depth deletion law with iterated-limit rate | Principal proposed contribution; no exact precedent located |
| Uniform weighted Fourier matching for moving full product pools | Principal technical novelty candidate; no exact precedent located |
| Explicit full-pool gcd bound | Supporting estimate; avoid claiming independent priority |
| Sum-versus-maximum TV comparison | Supporting lemma; avoid claiming independent priority |
| Another proof of PNT | Consequence; insufficient by itself to establish novelty |
| Better quantitative Mertens/PNT error | Not obtained or claimed |

## Changes made

Rewrote title and abstract; added a related-work subsection with precise source locations; added the elementary fixed-multiplier persistence remark; cited the short-interval estimate at its lemma; added seven bibliographic entries; aligned the scope paragraph. The main theorem and its proof estimates were not changed. The added remark was checked internally against the existing counting lemmas; no independent review of this revision is claimed.

## Remaining priority risk

The next decisive comparison would be an expert derivation attempt from the existing multiplier constructions or a general triangular-array convolution theorem with the required H-uniform constants. A focused search cannot certify absence of such a derivation. Until that comparison, use the concrete theorem statement and attributed method, and avoid “first,” “entirely new approach,” or “new elementary proof” in the title and abstract.
