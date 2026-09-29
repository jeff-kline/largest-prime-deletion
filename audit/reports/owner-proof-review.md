# Release owner's proof review

STAGE: PROOF-AUDIT (owner, INTERNAL-NONINDEPENDENT)
Date: 2026-09-28.
Revision: drafting source `consolidated-proof.tex`, SHA-256
`4f01b8a7b08749251fe1784ef1fc34c82283a6b6622cb7d9077a1a6d83bbf15b`, which is
mathematically identical to `paper/main.tex` at commit `d199bfb` (the release
edits there touch only the title block, one abstract sentence, one scope
sentence, and one added bibliography entry).

Exposure: the manuscript was read in full before the drafting-stage reviews
(`audit/drafting/INITIAL-LOCAL-REVIEW.md`, `audit/drafting/LOCAL-MATCHING-REVIEW.md`).
Those were read afterwards. The reviewer is the release owner, who also
integrates edits, so this is not a process-separated audit; the fresh audit is
`proof-audit.md`.

VERDICT: no correctness defect found. Every load-bearing step below was
re-derived.

## Steps re-derived

- **Lemma 2.1.** Writing a = r²s, the conditions are (r,ℓ)=1 and (s,ℓ)=1;
  the error is O(2^ω(ℓ)√x) from the coprime count plus O(√x) from the tail of
  Σμ(r)/r². The Euler factor gives x·Π_{p|ℓ} p/(p+1) = γn/Π(p+1). Correct.
- **Lemma 2.2.** Chebyshev bound, the factorial identity, and partial
  summation. Standard and correct.
- **Lemma 2.3.** Each prime in (X,σX] exceeds m=⌊X⌋ and k<X, divides
  C(m+k,k), and the entropy bound gives X·b(σ)+O_σ(log X). With σ=e^{2a},
  b = O(a(1+log(1/a))). Correct.
- **Lemma 2.4 and Remark 2.5.** Chebyshev on the count of divisors from a
  fixed prime set; P(Z<r) ≤ A/(A−r)² → 0. If a has at least K primes above
  P⁺(b), the first K deletions remove only primes of a. Correct.
- **Proposition 3.1.** TV(U,V_h) ≤ ½√(E D²/(E D)² − 1) by Cauchy–Schwarz.
  First-moment error O(√(R/n)). Second moment: ℓ = lcm ≤ R² < n and
  ℓ^{−1/2} ≤ R/ℓ give error O(R·G_h/√n) → 0 because ε < 1/2. Pair generation
  of V_h: the marginal of b differs from λ_h by o(1), and removing the
  coprimality condition costs Σ_{p|b} C/p = O_h(1/Y). Deletion: a prime of b
  outside the top K would give K+1 primes above n^{1/(K+1)} in ba ≤ n, a
  contradiction. So T^K(ba) = T^{K−d}(a) for h = d, and T^{K+1}(ba) = T^{K−d}(a)
  for h = d+1, including termination at 1. Nested uniform laws give
  TV(U_x,U_y) = 1 − Q(x)/Q(y) ≤ η + o(1). Correct, with implied constant 1 on η.
- **Lemma 4.1.** P(repeat) ≤ θ_h, so e_h ≥ (1−θ)H₀^h/h!. The inclusion bound
  P(S|b) ≤ (h)_r Π(1/p)/((1−θ)H₀^r), gcd = Σ_{S}Π(p−1), and Σ(p−1)/p² ≤ H₀
  sum to (e^{h²/H₀} − 1)/(1−θ)². Correct.
- **Lemma 5.1.** Given the lower h−1 order statistics, the top one has density
  1/(x log(β/v)) on [v,β]. The shifted density dominates on the overlap, so
  TV = min(1, log(1+A/v)/log(β/v)) ≤ log h / log(β/v). The second-largest
  log-uniform has density h(h−1)y^{h−2}(1−y), giving E = h/H. The maxima cross
  at d/(d+1) with TV d^d/(d+1)^{d+1} ≤ 1/(d+1). Correct.
- **Lemma 6.1.** f_n(x) = (L/(2aH_n))Σ_{|log p − Lx| ≤ a} 1/p. With Lemma 2.3,
  f_n ≤ C(1+log(1/a))/(H_n x)·(1+o(1)). J is absolute times (1+log(1/a)); the
  n-threshold depends on c, β, a. The second bound follows from ∫f_n = 1.
  Correct.
- **Lemma 6.2.** The arc mass is ≤ (J/H)[(α/π)(H+log 4) + O(1/(|t|c))];
  α = A/J makes it ≤ 1/2 for |t| > T₀, and rotation gives
  |φ| ≤ 1 − (1−cos α)/2. The seminorm identity: Plancherel with
  ∫|ĥ|² = 2π∫|h|² and ∫|e^{iu}−1|²/u² du = 2π, so C_F = 4π². For the
  high/high region, the algebraic bound |z^h − w^h| ≤ hκ^{h−1}|z−w| needs only
  the endpoints in the κ-disc. For the low-involved region, C¹ convergence on
  compacts (weak convergence plus a common compact support), then the
  T₀/(R−T₀) tail, with n → ∞ before R → ∞. Weighted Cauchy–Schwarz over
  [h(c−a/L), h(β+a/L)] gives a factor → H, which cancels 1/H. Result:
  ‖g‖₁ ≤ √2·hκ^{h−1}√(J+1) in the limsup. Correct and uniform in H.
- **Proposition 6.3.** With a = min(1/4, η/(2(d+1))), the jitter on equal
  jittered sums is at most (2d+1)a < η in actual logarithms. Conditional
  resampling recovers the i.i.d. tuple marginals. Distinctness costs
  C(h,2)n^{−c}/H_n. Forgetting order gives the harmonic law. J ≤ C(1 + log((d+1)/η)).
  Correct.
- **Section 7.** Everything is fixed before n → ∞. c > 1/(K+1) puts all
  factors above Y. Products are at most n^{(d+1)β} = n^{1/8}. Monotonicity in K
  is contraction under T_*. With d = ⌊(log K)^{1/4}⌋ and H = ½ log K: energy
  O(d/√H), tolerance O(1/d), continuous O(d log d/H + 1/d), smoothing o(1/d),
  total O((log K)^{−1/4}). Correct.
- **Section 8.** μ(T^K m) = (−1)^K μ(m) when ω(m) ≥ K+1. The difference of
  expectations is 2(−1)^K M/Q + o(1), and |difference| ≤ 2 TV, so
  limsup |M|/Q ≤ limsup TV. The factor of two is correct.

## Exposition notes (not correctness defects)

- O1. In Proposition 3.1 the "Cη" term holds with C = 1. Harmless.
- O2. Lemma 6.2 leaves C_F implicit (it equals 4π²). It cancels, so this is harmless.
