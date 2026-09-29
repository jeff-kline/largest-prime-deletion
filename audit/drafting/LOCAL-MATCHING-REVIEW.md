# Independent audit of local matching and smoothing

STAGE: PROOF-AUDIT
VERDICT: VERIFIED for the continuous comparison, general weighted smoothing lemma, harmonic-prime application, and the stated moving-multiplier criterion/energy bound. The final assembly into the workspace's target is subject to separately reading its exact statement; no novelty verdict is given.

Date: 2026-09-28. Initial isolated report: INITIAL-LOCAL-REVIEW.md,
SHA256 cff29f9b01e536ed9715ea26c608c2421310653e5c699756e847575709aab89e.
Its NOT-BROKEN verdict was sealed before seeing the proofs. This report is the subsequent substantive proof audit, not a promotion of failure-to-refute into verification.

## Reviewed revisions

* LOCAL-MATCHING-ATTACK.md: f3d845832df29c97e93983fcbd88aaefe4e1b2f0b9c1e4b61564e0b272ae94da.
* LOCAL-SMOOTHING.md: 2110d205bd54604fc22d3456f4f1ae24b8577213037013e0e42bfd7b83349910.
* COUPLING-CONSTRUCTION.md: 5e047020299af028be35abcdb494d60268856f78871c8f0668f92012b3970d4f.

I initially saw a smoothing revision using a stronger upper-bound sieve. The final reviewed revision replaces it with the binomial interval estimate and M=O(1+log(1/a)); the stronger sieve is not a dependency of this verdict.

## Continuous comparison

Conditioning on the lower h-1 order statistics leaves the maximum with normalized density 1/x on [v,beta]. Translating it by their sum A increases the density throughout the common support. Thus TV is precisely the mass lost from [v,min(v+A,beta)], including the disjoint-support case. The inequality A<=(h-1)v and the beta(h-1,2) law of log(v/c)/H give the claimed h log(h)/H. The h=1 case is exact separately. Adjacent maxima cross at d/(d+1) in uniform-log coordinates and have TV d^d/(d+1)^(d+1). These steps prove the exact stated adjacent-sum bound, with the TV convention of half L1.

## Weighted Fourier lemma: all load-bearing steps checked

For the general packet let densities be supported in [c/2,2beta], bounded by M/(Hx), converge weakly to q, and H>=1. Mass normalization implies M>=H/(H+log4)>=1/(1+log4). Increasing M to max(M,1) therefore changes it only by an absolute factor.

1. The envelope gives integral x f_n(x)^2 dx<=M/H. The periodic-arc estimate follows by integration by parts against 1/x: the zero-mean indicator has a periodic primitive bounded by an absolute constant, and the endpoint/variation error is O(1/(|t|c)). Taking an arc half-width alpha=A/M for a sufficiently small absolute A, and T sufficiently large, gives at most half the mass in any such arc. Rotating the characteristic function then gives kappa=1-(1-cos(alpha))/2, with 1-kappa>=C/M^2. All H dependence is absorbed using (H+log4)/H<=1+log4.

2. The exact homogeneous-seminorm identity follows from Tonelli and Plancherel applied to translations of the Fourier transform. The compactly supported densities and convolutions lie in L2, so there is no regularity assumption missing here. The seminorm is in the Fourier variable; it is not a claim that the original densities possess half a derivative.

3. On high-high pairs, write the increment of phi_n^h-phi^h as two separate increments and use |z^h-w^h|<=h kappa^(h-1)|z-w|. Squaring costs only the stated factor 2. Extending the resulting integrals to all pairs is legitimate by nonnegativity.

4. The remaining pairs really do tend to zero. Fixed compact support plus weak convergence gives uniform convergence of both characteristic functions and first derivatives on compact intervals (pointwise convergence and equicontinuity suffice). Hence compact diagonal pairs are bounded by a derivative supremum tending to zero. When one coordinate is in [-T,T] and the other exceeds R, the denominator gives the uniform O(T/(R-T)) tail. The correct order is n first, R second; T can be arbitrarily large but is fixed at this stage. No unproved uniform Fourier decay or diagonal domination is used.

5. Weighted Cauchy-Schwarz converts the weighted L2 defect into L1 with multiplier sqrt(H+log4) for the packet's general support, or sqrt(H+o(1)) for actual jittered primes. This cancels the factor 1/sqrt(H). The result is an absolute-constant bound C h sqrt(M+1) kappa^(h-1). The positive lower bound on M absorbs the h-1 shift and yields the packet form C h sqrt(M) exp(-c0 h/M^2), after absolute constant adjustment. This includes h=1, where the estimate need not be small.

Thus the proposed fractional-Sobolev high/low split is valid and has the claimed parameter uniformity. Its output is a limsup in n for each fixed tuple of parameters, not a simultaneous uniform rate in all parameters.

## Elementary prime inputs, discharged directly

These derivations avoid relying on the stronger sieve from the stale revision and require no PNT or cancellation of the Mobius function.

For fixed 1<sigma<2 and sufficiently large X, let m=floor(X), k=floor(sigma X)-m. Every prime X<p<=sigma X divides binomial(m+k,k): it occurs in the numerator (m+1)...(m+k), and exceeds both m and k. Therefore

    [pi(sigma X)-pi(X)] log X <= log binomial(m+k,k).

The binomial theorem, with probabilities m/(m+k) and k/(m+k), bounds this logarithm by

    (m+k)log(m+k)-m log m-k log k
      = X[sigma log sigma-(sigma-1)log(sigma-1)] + O_sigma(1).

An O_sigma(log X) remainder would also suffice. This proves the required upper bound. For sigma=exp(2a), 0<a<=1/4, the bracket is O(a(1+log(1/a))) with an absolute implied constant. The threshold may depend on fixed a. After putting X=exp(Lx-a), uniformity over x in the support follows from Lx tending uniformly to infinity. Multiplication by the reciprocal-prime weight and by L/(2aH_n) gives exactly M=O(1+log(1/a)), independent of H,c,beta.

For completeness the reciprocal-prime Mertens input also follows elementarily. The central binomial coefficient gives theta(2m)-theta(m)<=2m log2; dyadic summation gives theta(x)=O(x), and summing prime powers gives psi(x)=O(x). The factorial identity

    log(N!) = sum_{r<=N} Lambda(r) floor(N/r)

then implies sum_{r<=N}Lambda(r)/r=log N+O(1), because replacing floors costs at most psi(N)=O(N), and log(N!)/N=log N+O(1). The prime-power contribution of exponents at least two is bounded absolutely by sum_{p} log(p)/(p(p-1))<infinity. Thus A(x)=sum_{p<=x}log(p)/p=log x+O(1). Partial summation gives

    sum_{p<=x}1/p = A(x)/log x + integral_2^x A(t)/(t log(t)^2) dt
                 = log log x+B+O(1/log x).

The error integral converges absolutely at infinity, and its remaining tail is O(1/log x). This proves the input used for H_n and weak convergence.

## Return to discrete products and energy

The total jitter in degrees h,h+1 is at most (2h+1)a<eta with a=min(1/4,eta/[2(h+1)]). Maximal coupling of the absolutely continuous sum laws followed by their conditional tuple laws is valid on standard Borel spaces and recovers exactly the prescribed iid marginal tuple laws. On equality the original logarithms differ by less than eta. Distinctness conditioning costs at most binomial(h,2) max_p 1/(pH_n), and forgetting order gives the harmonic law on distinct degree-h products. Conditioning need not preserve the old coupling verbatim: attach maximal couplings of each original marginal to its conditioned marginal, adding the two o(1) failure probabilities.

Fix eta>0 first and take h large. Then M=O(1+log(h/eta)), so h sqrt(M) exp(-c h/M^2) tends to zero. After h is fixed choose H as large as needed, beta=epsilon/(h+1), c=beta exp(-H), and K with 1/(K+1)<c. Choose n last. This is a legitimate iterated-parameter construction; no quantitative n threshold uniform in h,H,eta is needed.

The full-pool energy proof is correct: collision control bounds e_h from below, inclusion probabilities bound each nonempty divisor term in gcd-1, and the exponential series yields the asserted excess-energy bound. The empty divisor contributes exactly 1. The resulting energy approaches 1 as H/h^2 increases.

The moving-multiplier criterion was also checked. Squarefree counting with divisor l has the displayed main term and O(2^omega(l)sqrt(n/l)) error by expanding the squarefree indicator and coprimality. In the second moment, sqrt(lcm(b,c))<=R yields error O_K(RG/sqrt(n)); epsilon<1/2 suffices. Conditional coprimality removal costs O_K(1/L). Since all multiplier primes exceed n^(1/(K+1)), they must occur among the first K deleted largest primes, establishing the exact-prefix identity, including termination at 1. Nested uniform squarefree laws produce the O(eta) term. In using this criterion, a log discrepancy eta gives ratio exp(eta); substitute its parameter exp(eta)-1=O(eta), not literally eta.

## Scope and resources

No fatal gap or unsupported analytic inference remains in the reviewed local arguments. This is a complete argument audit for those claims, including fresh elementary derivations of the prime inputs; it is not an independent novelty/literature review or a verification of any unexamined transfer to a different target. Sources retrieved: zero. Numerical experiments/Python workloads: zero. No agents spawned; no email or external communication. The initial report remains unedited.

## Final integration addendum

STAGE: PROOF-AUDIT (assembly)
VERDICT: VERIFIED for

    lim_{K->infinity} limsup_{n->infinity}
        TV(Law(T^K(U_n)),Law(T^(K+1)(U_n))) = 0,

where U_n is uniform on squarefree integers at most n, T removes the largest prime factor, and T(1)=1. Also VERIFIED: its consequence M(n)=o(n), and the stated ordered-limit positive-excursion/interior-mass consequences. PNT then follows by the explicitly named classical equivalence with M(n)=o(n); novelty is not assessed.

Additional exposure: LOCAL-MATCHING-ASSEMBLY.md, DEPTH-TRANSFER.md, DAMPING-RESULT.md. The assembly's tolerance selection leaves a valid margin; each d,H,c,beta,K is fixed before n tends to infinity. The monotonicity in K is precisely contraction of total variation under the same deterministic pushforward on both measures. It upgrades arbitrarily small bounds at chosen depths to the full depth limit.

For the direct Mobius test, outside omega(m)<K the parity identity is exact. The difference of expectations at depths K,K+1 is 2(-1)^K M(n)/Q(n)+o(1), while its absolute value is bounded by 2 TV. Thus the stated inequality for limsup |M|/Q has the correct factor. Here is a direct elementary justification of the exceptional density: for a fixed finite prime set P, Z(m)=sum_{p in P}1_{p|m} has limiting mean A=sum 1/p and variance sum (1/p)(1-1/p)<=A by residue counting. If omega(m)<K then Z(m)<K. For A>K, Chebyshev bounds its upper density by A/(A-K)^2, tending to zero as P grows and A diverges. Conditioning on squarefreeness costs only the positive limiting squarefree density. This uses no cancellation estimate.

For each fixed l, the positive nonroot difference of the two ancestor laws is D_l/Q. The discrepancy from their full TV is bounded by their root masses, which tend to zero. Thus D_l/n has limsup tending to zero as l grows. The paired recurrence yields P_alpha<=sum_l alpha^(2l-1)D_l. Dominated tails for fixed alpha, then a finite/tail split as alpha tends to one, prove (1-alpha)limsup_n P_alpha/n=0. The exact identity for the interior absolute mass in DAMPING-RESULT.md then proves the requested interior-mass ordered limit. No simultaneous alpha,n assertion was used.

### Quantitative depth consequence

For all sufficiently large integer K set

    d=floor((log K)^(1/4)), eta=1/d,
    H=(log K)/2, beta=1/[8(d+1)], c=beta K^(-1/2).

Then log(beta/c)=H, c>1/(K+1), and K>=d+1. Products in both degrees are at most n^(1/8). The two square-root excess energies are O(d/sqrt(H))=O((log K)^(-1/4)); the continuous discrepancy is O(d log(d)/H+1/d), and the ratio tolerance costs O(1/d). With the specified jitter, M=O(log d), so the smoothing term

    O(d sqrt(log d) exp(-c0 d/(log d)^2))

is o(1/d). All implied constants can be chosen absolute. Therefore

    limsup_{n->infinity} TV(nu_n,K,nu_n,K+1)
        = O((log K)^(-1/4)).

This is a bound on the iterated-limit quantity. The argument supplies no n threshold uniform in K and therefore no quantitative rate for M(n)/n. The quantitative consequence is verified analytically without numerical tests.

Assembly-audit revision hashes:
* LOCAL-MATCHING-ASSEMBLY.md: bf11e63c1836d52349fcd404ae29bb4d7b7c0984442806a9c56579dea0acdbb5.
* DEPTH-TRANSFER.md: 39a3d7ed5f6fb17c0a3902a2e0d34a1392010ee859aac91e94566a11e07c978f.
* DAMPING-RESULT.md: 3bf818cddc2f1fd3aaddeda376801a265f3be61e3aaaa4e32729780f2089e83c.
