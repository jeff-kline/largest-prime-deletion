# Stage 2 proof audit: "Total variation under largest-prime deletion" v0.1.0

```text
STAGE: PROOF-AUDIT
VERDICT: VERIFIED
CLAIM: Theorem 1.1 (for all sufficiently large K, with an absolute constant C,
  limsup_n TV(nu_{n,K}, nu_{n,K+1}) <= C (log K)^{-1/4}, and hence the double
  limit is 0) and Corollary 1.2 (M(n) = o(n)), as stated in main.tex at commit
  d199bfb, sha256 3533d5f0ec0aa061a8208dbb8be589fec1b4845c23c0aeebe822545b35f0b519.
EVIDENCE: I checked every load-bearing step from the definitions (l.31-55) to
  Sec. 7 (l.506-541) and Sec. 8 (l.545-562) by hand. I found no unsupported
  inference. All findings below are exposition-level (optional or should-fix).
  None is a correctness defect.
COVERAGE: Lemmas 2.1-2.4, Remark 2.5, Prop 3.1, Lemma 4.1, Lemma 5.1, Lemmas
  6.1-6.2, Prop 6.3, Sec. 7 (qualitative and quantitative), Sec. 8, and the
  prose claims in the abstract and Secs. 1, 1.1 and 9. Not covered: the
  bibliographic and prior-art assertions (l.82-92, and the "cf. Richter
  Lemma 3.3" attribution at l.161); I did not open the cited sources. I did not
  compare main.pdf against main.tex.
DEPENDENCIES: Discharged inside the paper: squarefree counting, the Mertens-type
  estimate, the Chebyshev-type short-interval bound, and the scarcity of
  integers with few prime factors. External standard facts, all correctly used:
  Plancherel; Tonelli; weak convergence with common compact support implies
  C^1-uniform convergence of the characteristic functions on compacts (via
  equicontinuity); the existence of maximal couplings, regular conditional
  laws and gluing. Remaining obligations: none.
ERRATA: No correctness defects. Exposition items are listed in the table.
EXPOSURE: Only the frozen main.tex at d199bfb. No earlier reviews, drafting
  notes or other audit reports were read. This audit had no Stage 1 packet or
  initial report.
RESOURCES: Single agent; roughly one full read of main.tex plus a line-by-line
  derivation check. One Python one-liner in ~/.venvs/claude checked two
  constants: the integral of |e^{iu}-1|^2/u^2 is 2*pi, so C_F = 4*pi^2; the
  maximum TV d^d/(d+1)^{d+1}; and the redundancy of the min in a. A finite check
  like this does not verify any limit claim.
```

## Checked chain (summary of what was verified)

**Sec. 1 facts (l.46-55).** The maximal-coupling construction is exact: the residual masses are mutually singular. Contraction under pushforward holds, and |E_P f - E_Q f| <= 2 TV holds for |f| <= 1.

**Lemma 2.1 (l.96-122).** Only r coprime to ell contribute. Each r <= sqrt(x) incurs an error of O(2^{omega(ell)}), which totals O(2^{omega(ell)} sqrt x). Extending the sum costs x * sum_{r > sqrt x} r^{-2} = O(sqrt x). The simplification (1-1/p)/(1-1/p^2) = p/(p+1) gives n / prod(p+1). The implied constant is absolute.

**Lemma 2.2 (l.124-159).** The Chebyshev bound via binom(2m, m), the psi(x) = O(x) step, log N! with the floor error at most psi(N), the prime-power tail, and partial summation all check. The E-integral converges with tail O(1/log x).

**Lemma 2.3 (l.161-181).** Primes in (X, sigma X] exceed both m and k once X is large, because sigma < 2. The entropy bound on binom(m+k, k) and the perturbation of (m, k) by O(1) giving O(log X) both check. On b(e^{2a}) <= C a (1 + log(1/a)) for a <= 1/4: sigma - 1 <= e^{1/2} - 1 < 1, so both terms are nonnegative and of the stated size.

**Lemma 2.4, Remark 2.5 (l.183-201).** The covariances tend to 0, and Chebyshev gives the upper density bound A/(A-r)^2. The top-K argument in the remark is correct.

**Prop 3.1 (l.205-283).**
- The Cauchy-Schwarz bias bound is correct.
- First moment: the error is (sum w_b / sqrt b) / Z_h <= sqrt(R) Z_h / Z_h, so the normalized error is O_h(sqrt(R/n)).
- Second moment: ell = lcm(b, c) <= bc <= R^2 < n, and ell^{-1/2} <= R/ell is equivalent to ell <= R^2. Since sum w_b w_c / lcm = Z_h^2 G_h, the error is C_h R G_h / sqrt n = o(1), because epsilon < 1/2 and G_h is bounded. Also prod(p+1) = ell (1 + O_h(1/Y)).
- The pair representation of V_h is exact: the mass of m is proportional to the sum over b dividing m of w_b.
- The b-marginal has relative error O_h(1/Y) + O_h(sqrt(R/n)) uniformly in b.
- The coprimality defect is at most h C / Y, uniformly for x >= n/R.
- Deletion: a prime of b that is not among the top K would force K+1 prime factors each larger than n^{1/(K+1)}, contradicting ba <= n. The top-K set is an up-set containing every prime of b, so T^K(ba) = T^{K-d}(a) when h = d, and T^{K+1}(ba) = T^{K-d}(a) when h = d+1. This includes the case where the process reaches 1: then omega(a) < K - d and both sides equal 1.
- Nested cutoffs: TV(U_x, U_y) <= 1 - e^{-eta} + o(1) uniformly for x, y >= n/R.
- The five-term triangle inequality through M_h = integral of T^{K-d}_* U_{n/b} d lambda_h(b) gives (3.x). The constant C in C eta can be taken to be 1.

**Lemma 4.1 (l.287-321).**
- The collision union bound gives at most theta_h.
- Also e_h >= (1 - theta) H_0^h / h! and e_j <= H_0^j / j!.
- The divisibility probability is bounded by (h)_r / ((1 - theta) H_0^r) times prod_{p in S} 1/p.
- The gcd expansion over subsets, independence, and e_r(x) <= (sum x)^r / r! (step left implicit; see F4) give (4.x).
- theta_h < 1 forces e_h > 0.

**Lemma 5.1 (l.331-363).**
- Conditional on the lower h-1 order statistics, the maximum has density 1/(x log(beta/v)) on [v, beta].
- For a shift A <= (h-1)v, the TV is exactly min(1, log(1 + A/v) / log(beta/v)).
- The second-largest uniform has density h(h-1) y^{h-2} (1-y), so E[1/(H(1-Y))] = h/H.
- The maxima laws cross once, and their TV is d^d / (d+1)^{d+1} <= 1/(d+1).

**Lemma 6.1 (l.382-401).**
- The jittered density formula is correct.
- Lemma 2.3 applies with X = e^{Lx-a} >= n^c e^{-2a}, which tends to infinity uniformly.
- The endpoint and O_a(1) contribution is O_a(L n^{-c}) = o(1/(Hx)).
- H_n -> H by Lemma 2.2.
- J = C(1 + log(1/a)) depends only on a. Only the threshold in n depends on (c, beta, a).
- The integral bound follows from f_n <= J/(Hx) and the integral of f_n being 1. The integral of x q^2 equals 1/H.

**Lemma 6.2 (l.405-476).**
- *Step 1.* Integration by parts against the bounded primitive gives the error O(1/(|t|c)). Because H >= 1, taking alpha = A/J with A absolute makes the arc mass at most 1/2 for |t| > T_0(c, H, J). The rotation argument gives kappa = 1 - (1 - cos alpha)/2, so 1 - kappa >= c_0 / J^2 with c_0 absolute. kappa is independent of c, beta, H and n.
- *Step 2.* The substitution t = s + r, Plancherel with the factor 2 pi, Tonelli, and the scaling u = rx give C_F = 2 pi * 2 pi = 4 pi^2. This matches the numeric check.
- *Step 3, high/high region.* |z^h - w^h| <= h kappa^{h-1} |z - w| and (x + y)^2 <= 2x^2 + 2y^2 give a bound of 2 C_F h^2 kappa^{2h-2} (J + 1) / H, which is uniform in n and R.
- *Step 3, low region.* [-R, R]^2 together with the strips {|s| <= T_0, |t| > R} and their transposes covers every pair with a coordinate in [-T_0, T_0], because R > T_0. On [-R, R]^2 the contribution is at most 4R^2 sup |u_n'|^2 -> 0. The strips contribute at most 16 * 4 T_0 / (R - T_0). The order of limits (n first, then R) is valid.
- *Step 3, conclusion.* Dividing by C_F and applying Cauchy-Schwarz with the log-width tending to H cancels H exactly. The result is limsup ||g||_1 <= sqrt(2) h sqrt(J + 1) kappa^{h-1}.

**Prop 6.3 (l.478-502).**
- The triangle inequality through q^{*d} and q^{*(d+1)} gives (6.x), including the factor (d+1) and kappa^{d-1} <= exp(-c_0 (d-1) / J^2).
- The maximal coupling of the jittered sums, followed by independent conditional resampling of (prime tuple, jitters), reproduces both original marginals exactly.
- On equal sums, |log B - log C| <= (2d+1) a = (2d+1) eta / (2d+2) < eta.
- The repetition probability is at most binom(h, 2) n^{-c} / H_n.
- Gluing to the distinctness-conditioned laws (TV = P(repeat)) gives exact marginals lambda_d and lambda_{d+1}.

**Sec. 7 (l.506-541).** Everything (tau, eta, d, H, epsilon = 1/8, beta, c, K) is fixed before n -> infinity.
- Products are at most n^{(d+1) beta} = n^{1/8}, and every factor exceeds n^c > n^{1/(K+1)}.
- Adjacent TV is monotone in k because nu_{n,k+1} = T_* nu_{n,k}.
- Quantitative choices:
  - H = (1/2) log K >= 1, and c > 1/(K+1) for large K.
  - The energies are O(d / sqrt H) = O((log K)^{-1/4}), since (d+1)^2 / H -> 0.
  - The term d log d / H = O((log K)^{-3/4} log log K).
  - The terms eta = 1/d and 1/(d+1) are Theta((log K)^{-1/4}); this is the binding term.
  - a = 1/(2d(d+1)) and J = O(log d), so the smoothing term is O(d sqrt(log d) exp(-c' d / log^2 d)) = o(1/d).
- All implied constants are absolute, and the threshold on K is absolute.

**Sec. 8 (l.545-562).** For omega(m) >= K+1, mu(T^K m) - mu(T^{K+1} m) = 2(-1)^K mu(m). The difference of expectations is 2(-1)^K M(n)/Q(n) + o(1), and |E f - E g| <= 2 TV. So |M|/Q <= TV + o(1). The factor of two is handled correctly.

**Prose.**
- Abstract l.26: every claim matches the proof, including "no prime number theorem assumed", "no rate for M(n)/n" and the H-independent constants.
- l.78 and l.568 correctly disclaim uniformity in n.
- l.88 ("H >> d^2") matches the choice H = (1/2) log K, d^2 ~ (log K)^{1/2}.
- l.84 ("tests chosen separately for each n") is true of a supremum-over-sets TV bound.
- I found no overstatement of what is proved. The prior-art characterizations are unchecked (see COVERAGE).

## Findings

| id | severity | line | finding | suggested fix |
|---|---|---|---|---|
| F1 | optional | 488, 537 | `a = min(1/4, eta/[2(d+1)])`: because eta <= 1 and d >= 1, eta/[2(d+1)] <= 1/4 always holds, so the min is inert. "for large d" at l.537 is likewise unnecessary. | Write `a = eta/[2(d+1)]` (and note that a <= 1/4). Delete "for large d". |
| F2 | optional | 264, 506 | The letter `c` is reused for an unrelated constant (`Q(x) >= cx`; `exp(-c d/log^2)`) while `c` is the window endpoint throughout Secs. 5-7. The prose convention at l.78 covers only `C`, `c_0`. | Use `c_1` or `c_0` in both places. |
| F3 | optional | 463 | `R` is reused as a frequency cutoff, while `R = n^epsilon` in Sec. 3. | Rename the cutoff, e.g. `T_1`. |
| F4 | optional | 316-320 | The step from the sum over S of prod (p-1)/p^2 to H_0^r / r! also needs e_r(x) <= (sum x)^r / r!. Only `sum (p-1)/p^2 <= H_0` is cited. | Add "and e_r(x) <= (sum_p x_p)^r / r!". |
| F5 | optional | 305 | The notation `P(S | b)` reads as a conditional probability. It means P(prod_S p divides b). | Write `P(S subset b)` or `pi_S`. |
| F6 | optional | 226, 280 | The proof gives `C = 1` in `C eta`, which Theorem 1.1's "absolute C" needs anyway. | State `+ eta` or note C = 1. |
| F7 | optional | 437-451 | `C_F` is left implicit. It equals 4 pi^2 (2 pi from Plancherel times the integral of \|e^{iu}-1\|^2/u^2 du, which is 2 pi). | Optionally state C_F = 4 pi^2. It cancels, so this is cosmetic. |
| F8 | optional | 463 | The test function `i x e^{itx}` is unbounded on R. Weak convergence applies only after truncating to the common compact support, which the text invokes without making explicit. | Add "(after truncation to [c/2, 2 beta])". |
| F9 | optional | 566 | "Complete modulo standard measure-theoretic facts and Plancherel". The argument also uses equicontinuity and Arzela-Ascoli-type uniformity and regular conditional laws, both standard. | Optionally list them. |
| F10 | optional | 423 | `T_0(c, beta, H, J)` is redundant, since beta = c e^H. | Harmless; leave as is or write `T_0(c, H, J)`. |
| F11 | should-fix (unverified, not a math defect) | 82-92, 161 | The prior-art characterizations (Richter Props 2.1-2.2 and Lemma 3.3; BR Prop 2.1, Lemmas 2.2-2.3, Cor 1.8; LWWY Thms 1.2 and 1.7; Arratia Sec. 3.4.1; NP Thm 1.2) were outside this audit's reading scope and were not checked. | Route them to a citation audit before release. |

No must-fix items. No GAP or REFUTED findings.
