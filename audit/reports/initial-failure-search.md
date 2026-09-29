# Cold examiner: initial failure search

```text
STAGE: INITIAL
VERDICT: NOT-BROKEN
```

No concrete failure was found in the Theorem, the Corollary, or intermediate
statements 1 to 5 as stated. This is not a proof and not a confirmation. The one
substantive finding concerns scope, not correctness: statement 4 on its own
implies that zeta(1+i gamma) != 0 for every real gamma != 0. The elementary
difficulty of the prime number theorem therefore sits entirely inside statement
4's unseen proof. That is where a Stage 2 audit should concentrate.

## EVIDENCE

### E1. Corollary: the deduction and its factor of 2 check out

For squarefree N with omega(N) >= K+1:
- mu(T^K N) = (-1)^K mu(N);
- mu(T^{K+1} N) = (-1)^{K+1} mu(N). This includes omega = K+1, where
  T^{K+1}N = 1 and mu(N) = (-1)^{K+1}.

So mu(T^K N) - mu(T^{K+1} N) = 2(-1)^K mu(N) on that event. With TV defined as
sup_A (half the L1 distance), and |mu| <= 1, we have
|E f(P) - E f(Q)| <= 2 TV. This gives

    |E mu(N_n)| <= TV(nu_{n,K}, nu_{n,K+1}) + 3 P(omega(N_n) <= K).

For fixed K, P(omega(N_n) <= K) -> 0. This follows elementarily, for example
from Turan's variance bound. Because M(n) = Q(n) E mu(U_n) and Q(n) ~ 6n/pi^2,
limsup |M(n)|/n <= (6/pi^2) C (log K)^{-1/4} for every large K. Hence
M(n) = o(n).

The factor 2 helps rather than hurts. There is no TV-convention mismatch: under
the half-L1 convention the constants work.

**Scope note.** M(n) = o(n) is equivalent to the PNT (Landau). The package is
therefore a claimed elementary proof of the PNT. That claim is not false, but it
is strong.

### E2. Parameter choice does yield (log K)^{-1/4}

Checked by hand:

| Check | Result |
|---|---|
| c = beta K^{-1/2} > 1/(K+1), so the primes exceed Y | Holds once K+1 > 8(d+1) sqrt K |
| Products of <= d+1 primes are <= n^{beta(d+1)} | = n^{1/8} = n^eps, with eps < 1/2 |
| H = log(beta/c) | = (1/2) log K >= 1 for K >= e^2 |
| K >= d+1 | Holds |
| delta = n^{-c} -> 0 | So theta_h -> 0 |
| Mertens gives H_0 -> H | Holds |

The terms of the bound:
- **Statement 2 term.** (1/2)sqrt(G_h - 1) ~ (1/2)sqrt(h^2/H) ~ 2^{-1/2}(log K)^{-1/4}.
- **Statement 5 first term.** O((log K)^{-3/4} log log K).
- **1/(d+1) and C eta = C/d.** Both are ~ (log K)^{-1/4}.
- **Last term of statement 5.** J = O(log d) = O(log log K), so the exponent is
  -c'(log K)^{1/4}/(log log K)^2. This beats any power of log K for large K.

The claimed rate follows from statements 1, 2 and 5. The threshold for
"sufficiently large K" is astronomically large, but it exists.

Statement 5's form is consistent with statements 3 and 4 via the triangle
inequality:

    TV(f^{*d}, f^{*(d+1)}) <= TV(q^{*d}, q^{*(d+1)}) + (1/2)||f^{*d} - q^{*d}|| + (1/2)||f^{*(d+1)} - q^{*(d+1)}||

Here kappa^{d-1} <= exp(-(1-kappa)(d-1)), and a is inferred to be ~ eta/(d+1).
That inference matches J <= C(1 + log((d+1)/eta)).

### E3. Statement 3: exact identity for the max term, Monte Carlo for the sum term

In U = (log X - log c)/H coordinates, A_h has density h u^{h-1} on [0,1]. So

    TV(A_d, A_{d+1}) = max_u u^d(1-u) = d^d/(d+1)^{d+1}

exactly. The second inequality in statement 3 is then the triangle inequality
applied to the first.

Monte Carlo on TV(S_h, A_h) against the bound h log h / H (4e6 samples, 300 bins
in log space) found no violation:

| h | H | TV | Bound |
|---|---|---|---|
| 2 | 2 | 0.34 | 0.69 |
| 2 | 20 | 0.0064 | 0.069 |
| 3 | 3 | 0.42 | 1.10 |
| 5 | 8 | 0.21 | 1.01 |

Observed TV decays roughly like H^{-1.6} for h = 2, faster than the claimed 1/H.
(Script: probe_s3.py.)

### E4. Statement 2: brute force found no violation

Exact computation used gcd(b,c) = sum_{e | b, e | c} phi(e), so
G = sum_e phi(e) P(e | B)^2.
- About 400 random prime sets (3 to 11 primes drawn from the first 12 to 400
  primes), with h = 1 to 3 and theta_h < 1: the maximum of (G-1)/bound was 0.51.
- Structured cases (40 smallest primes with h = 2, 3; 150 primes > 500 with
  h = 2): G - 1 was far below the bound.

Heuristic support for the shape of the bound: the coefficient of H_0^{-k} in
exp(h^2/H_0) is h^{2k}/k!, which is at least (h!/(h-k)!)^2/k!. That is the count
of k-fold coincidences. (Script: probe_s2.py.)

### E5. Statements 4 and 5 hold as stated (PNT granted), with constants independent of H

This inference uses the PNT, a known theorem, as a truth oracle. It does not use
the claimed proof. With the PNT in hand:
- In each jitter window [n^u e^{-a}, n^u e^{a}], the 1/p mass is
  ~ 2a/(u log n) (1 + o(1)). So f_n -> q in L1 and the limsup in statement 4 is 0.
- Local counts of products of h primes at log-resolution eta converge to the
  continuous density. So the minimal coupling failure probability in statement 5
  is at most TV(q^{*d}, q^{*(d+1)}), which is at most the stated right-hand side.

So statements 4 and 5 are true with any positive constants. Their H-independence
cannot be refuted. The only live question is whether the proof avoids the PNT,
and that is Stage 2 material.

### E6. Scope finding: statement 4 contains the full non-vanishing of zeta on Re s = 1 (UNRESOLVED as a proof-risk only)

Let rho(xi) be the characteristic function. Then
||f^{*h} - q^{*h}||_1 >= sup_xi |rho_f(xi)^h - rho_q(xi)^h|.

Suppose zeta(1 + i gamma0) = 0 for some gamma0 != 0. The zero is necessarily
simple, since the ratio is at most 1. Then, at xi_n = gamma0 log n:
- (1/H) sum_{n^c < p <= n^beta} p^{-1-i gamma0} -> -1;
- so |rho_{f_n}(xi_n)| -> |sinc(a gamma0)| >= 1 - (a gamma0)^2/6;
- meanwhile rho_q(xi_n) -> 0.

Letting h -> infinity in statement 4 forces |sinc(a gamma0)| <= kappa <= 1 - c_0/J^2
with J ~ log(1/a). This fails once a is small enough that
(a gamma0)^2/6 < c_0/(C^2 log^2(1/a)). So statement 4, for all a in (0, 1/4],
implies zeta(1 + it) != 0 for all t != 0.

This is consistent with truth. It shows that statement 4's claimed elementary
proof (Chebyshev, Mertens, Plancherel) must contain an argument of
Selberg-Erdos or Halasz strength that rules out p^{i gamma} "pretending" to be a
constant phase at every height gamma up to ~ 1/(a log(1/a)).

Chebyshev-type bounds control only dyadic or constant-ratio windows. They do not
by themselves bound oscillation at frequency gamma > ~ 1/log 2 in log p. A
Stage 2 audit should check exactly how 1 - kappa >= c_0/J^2 is obtained for the
large-gamma range, and whether the jitter plus some doubling or tripling trick
(for example 1 - Re z^2 <= 4(1 - Re z) applied along p^{i k gamma}) really
closes it without the PNT.

This is not a demonstrated gap. It is the place where a gap would have to be.

### E7. The Theorem is plausibly true, with a better true rate

This inference was not rigorously checked. By the exact identity

    nu_{n,K}(m) = Q(n)^{-1} #{b : b is a product of K distinct primes > P^+(m), b <= n/m}

(up to a negligible omega < K term), nu_{n,K}(m) depends on m only through
(m, P^+(m)), and the same holds for K+1. Under the PNT, the n -> infinity limit
of the TV then equals the TV between the Poisson-Dirichlet(1) laws of
(R_K, L_{K+1}) and (R_{K+1}, L_{K+2}). Here R_K is the mass remaining after
removing the K largest parts.

Via the Poisson-process representation, R_K / L_{K+1} has asymptotically the
same (Dickman-type) law for K and K+1. The difference reduces to
TV(Gamma(K+1), Gamma(K+2)) = Poisson(K+1) pmf at K+1 ~ (2 pi K)^{-1/2}.

So the heuristic true limit is O(K^{-1/2}), well below the claimed
C(log K)^{-1/4}. There is no tension, and nothing in the rate secretly implies
a known-false statement.

### E8. Statement 1 architecture is plausible, and small-K cases are vacuous

Any bm <= n has at most K prime factors > n^{1/(K+1)}. So if b has d primes
> Y, then T^K(bm) = T^{K-d}(m) exactly, and likewise
T^{K+1}(cm) = T^{K-d}(m) for c with d+1 primes > Y. This supports the
multiplier-transfer design.

The sqrt(G - 1) error has the standard Cauchy-Schwarz (Turan-Kubilius) shape,
with E w^2 ~ sum lambda lambda gcd. The coprimality and Q(n/b) ~ (6/pi^2) n/b
corrections are uniform because b <= n^eps and the primes exceed Y -> infinity.
So "moving multiplier sets" do not obviously break the o(1).

Lower bound: by Cauchy-Schwarz on G = sum_e phi(e) P(e | B)^2,

    G_h - 1 >= h^2 / sum_{Y < p <= n^eps} 1/(p-1) ~ h^2 / log(eps(K+1))

So statement 1 can never certify a TV below ~ d/sqrt(log K). That is consistent
with E7 and gives no contradiction.

Degenerate case: for K+1 <= 2(d+1)/eps, the set B_{d+1} is empty. Z = 0 and
lambda is undefined, so the hypothesis cannot be met and the statement is
vacuous. The same holds for K = 2, 3, and for K = 4 with d = 1, where the
right-hand side exceeds 1. The requirement that the sets be nonempty is implicit.
It is a cosmetic hypothesis to state, not a failure.

## Probes

- Corollary parity algebra and factor 2 (hand): **passes**. The bound is TV + o(1), with no loss.
- Parameter bookkeeping for (log K)^{-1/4} (hand): **passes**. The dominant terms are 1/(d+1), C/d and sqrt(G-1).
- Statement 3, max-term identity (exact): **passes**. It equals d^d/(d+1)^{d+1}.
- Statement 3, TV(S_h, A_h) Monte Carlo over 24 (h, H) pairs: **no violation**, with a margin of at least 1.8x everywhere.
- Statement 2, exact brute force on about 400 random and 3 structured prime sets: **no violation**. The maximum ratio was 0.51.
- Statements 4 and 5 against the PNT as oracle: **true as stated**. The limsup is 0, so the constants are trivially H-independent.
- Statement 4 against a hypothetical zeta(1 + i gamma) = 0: **statement 4 implies non-vanishing on Re s = 1**. This is a scope flag and UNRESOLVED as a proof-risk.
- Theorem true-limit heuristic through Poisson-Dirichlet(1): **consistent**. The true limit is ~ K^{-1/2}, below the claim.
- Statement 1, degenerate small K / empty B_{d+1}: **vacuous**, with an implicit nonemptiness hypothesis.
- Statement 1, lower bound on G: **consistent**. No certified bound falls below the true TV.

## COVERAGE

Tried:
- the Corollary's logic and constants;
- the TV convention;
- the rate arithmetic;
- the parameter admissibility constraints (Y, eps, H >= 1, K >= d+1, theta -> 0);
- statements 2 and 3 numerically;
- statements 4 and 5 against the PNT and against a hypothetical zero on Re s = 1;
- the plausibility of the Theorem's true limit;
- degenerate cases of statement 1.

Unchecked:
- Any proof, since proofs were withheld.
- Whether statement 4's kappa bound is attainable without the PNT. This is the
  principal proof-risk.
- Uniformity of the o(1) in statement 1 when B_h(n) moves with n. The
  architecture was examined, not the argument.
- The constant C in statement 1 and its absoluteness.
- Statement 3's first inequality for large h relative to H, beyond the
  Monte Carlo range. The bound is trivial there anyway.
- Rigorous justification of the Poisson-Dirichlet limit in E7.

## DEPENDENCIES

- **Used as known facts, not re-verified from sources:**
  - Landau's equivalence M(n) = o(n) <=> PNT;
  - the PNT with error o(1/log x) in sum 1/p;
  - Mertens' second theorem;
  - Turan / Hardy-Ramanujan concentration of omega;
  - zeta(1 + it) != 0 and the simplicity argument via |p^{-it}| = 1;
  - the Poisson-Dirichlet(1) Poisson-process representation (intensity x^{-1}e^{-x}, independent Gamma sum).
- **Unresolved:** whether statement 4 is provable from Chebyshev, Mertens and
  Plancherel alone.

## EXPOSURE

- **Material read.** Statement packet revision "derived from commit d199bfb,
  paper/main.tex sha256 3533d5f0...b519", and the cold-examiner SKILL.md.
- **Material not read.** No other repository file was read, including the two
  existing reports in this directory, whose names were seen in a directory
  listing. No web or online sources were used.
- **Tools.** An isolated virtual-environment Python [local path redacted 2026-09-28] ran
  probe_s3.py and probe_s2.py in a scratch directory; the scripts are not part of this release and the probes are unreproduced.
- **Independence.** This was a same-model context, with the shared-prior caveat.

## RESOURCES

- Two small computations, each under about a minute of CPU.
- Hand analysis otherwise.
- No subagents.
