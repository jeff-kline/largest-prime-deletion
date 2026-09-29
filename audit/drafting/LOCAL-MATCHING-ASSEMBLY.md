# Assembly of the local coupling and prefix limit

2026-09-28. Complete candidate argument submitted to cold review.
No novelty or release claim. Classical elementary positive-prime estimates
are inputs; no PNT, zero-free region, or Mobius cancellation is an input.

## Quantified theorem sought

For uniform squarefree m<=n (including1), T(m)=m/P+(m), T(1)=1,
and nu_n,k=Law(T^k(m)),

    lim_{k->infinity} limsup_{n->infinity}
        TV(nu_n,k,nu_n,k+1) = 0.

Conventions: TV is half L1, or sup over measurable sets. Limits are in
the displayed order; no assertion uniform for k growing with n.

## Inputs already checked or now submitted

A. COUPLING-CONSTRUCTION.md (prior cold review): moving squarefree degree
d,d+1 product laws, with all factors>n^(1/(K+1)), products<=n^epsilon,
epsilon<1/2, have exact prefix transfer. Harmonic-size coupling with log
distance<=eta outside massrho bounds TV(nu_K,nu_K+1) by
half-sqrt(Gd-1)+half-sqrt(Gd+1-1)+rho+C eta+o_n(1).
Log distanceeta means ratio at mostexp(eta); for eta<=1, exp(eta)-1<=2eta,
absorbed into C. G denotes E gcd under independent harmonic draws.

B. Same file, prior cold review: full prime-product pools with reciprocal
prime mass H_n and largest reciprocal delta_n satisfy
G_h-1 <=(exp(h²/H_n)-1)/(1-binom(h,2)delta_n/H_n)².

C. LOCAL-MATCHING-ATTACK.md (submitted this round): for density q(x)=1/(Hx)
on[c,beta], H=log(beta/c), adjacent sum laws satisfy
D_d(H)<=A_d/H+1/(d+1), A_d=dlogd+(d+1)log(d+1).

D. LOCAL-SMOOTHING.md (submitted this round): for prime pool
(n^c,n^beta], the distinct degree-d,d+1 harmonic laws admit log-distance
eta coupling with failure limsup bounded by

    D_d(H)+C(d+1)sqrt(M+1) exp(-c0(d-1)/M²),

where M<=C1(1+log((d+1)/eta)) and all C,c0,C1 absolute for H>=1.
Proof uses bounded jitter, a Fourier half-derivative seminorm, weighted
Cauchy-Schwarz, and elementary reciprocal-prime/short-interval estimates.
Constants in how large n must be may depend arbitrarily on fixed params.

## Parameter order closes the target if C,D pass review

Given target tolerance tau>0, first choose eta>0 small enough that the
O(eta) cutoff term is below tau/4. Fix this eta. Choose d large so that
1/(d+1) plus the smoothing error in D is below tau/4; this is possible
because d/log²(d/eta) grows faster than log d. Next choose finite H>=1
so large that A_d/H and the two square-root energy terms from B total
less than tau/4. Set epsilon=1/8, beta=epsilon/(d+1), c=beta exp(-H).
Choose fixed integer K>=d+1 with 1/(K+1)<c. Only now let n grow.

Elementary reciprocal-prime Mertens gives H_n->H; delta_n<=n^-c->0.
Both pool degrees are squarefree, all factors exceed the required
threshold, and their products are<=n^epsilon. Distinct-draw conditioning
costs o_n(1), already covered by D. Thus A yields limsup_n adjacent TV
at depthK below tau (allowing the unused tau/4 margin).

For each n, nu_n,k+1=T_*nu_n,k, and TV contracts under deterministic
pushforward. Consequently limsup_n adjacent TV is nonincreasing in k.
An arbitrarily small bound at some fixedK for each tau forces its limit
as k tends to infinity to be zero. This proves the stated target.

## Direct PNT consequence and a second check on the bridge

Let mu(m)=(-1)^omega(m) on squarefree m and zero otherwise, and
M(n)=sum_{m<=n}mu(m). For each fixedk,

    E_n[mu(T^k(m))]=(-1)^k M(n)/Q(n)+o_n(1).

Indeed the equality is exact for omega(m)>=k; the exception omega(m)<k
has density zero among squarefree integers. This zero-density fact is
elementary: finite-prime divisibility counts and divergence of sum1/p
show integers with bounded omega have zero density; Q(n)~6n/pi².
Since mu is a bounded test function,

    limsup_n |M(n)|/Q(n)
      <= limsup_n TV(nu_n,k,nu_n,k+1).

Let k tend to infinity. The target implies M(n)=o(n), hence PNT by the
classical elementary equivalence. The independent argument to M=o(n)
does not use the earlier PNT-dependent Dickman approximation or rate.

## Original damping target

For each fixedk and j>1, Q(n)nu_n,k(j)=C_k(n,j). Root mass is
#{squarefree m<=n:omega(m)<=k}/Q(n)=o(1). Hence
D_l(n)/Q(n) differs by o(1) from adjacent TV at depths2l-1,2l.
The proved prefix limit would give d_l=limsup_n D_l(n)/n->0.
DEPTH-TRANSFER.md then bounds P_alpha by its geometric weighted sum,
giving the original ordered-limit excursion condition and the damped
residual certificate. These are consequences of the same chain, not
additional independent proofs or stronger quantitative rates.
