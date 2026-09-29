# Fine-scale smoothing of harmonic prime products

2026-09-28. Worker proof, awaiting independent review. No numerical work,
new dependencies, or source retrievals. The analytic lemma below supplies
the previously missing upgrade from exponent-scale convergence to
fixed-logarithmic-resolution matching. Its two classical elementary
prime inputs are stated explicitly; neither is PNT or Möbius cancellation.
The continuous adjacent-degree comparison is the other worker's result.

## Elementary prime inputs

Use the following classical elementary estimates, with absolute constants:

1. Reciprocal-prime Mertens theorem:
   `sum_{p<=X} 1/p = log log X + B + O(1/log X)`.
2. Elementary binomial short-interval upper bound (Richter Lemma 3.3):
   `pi(sigma X)-pi(X) <= B(sigma) X/log X + O(1)`, where
   `B(sigma)=sigma log sigma-(sigma-1)log(sigma-1)`.
   We use fixed `sigma=exp(2a)>1` before X tends to infinity.

The first theorem concerns a positive reciprocal-prime sum, not the
Mertens function `sum mu(m)`. Both admit classical elementary proofs.
A complete self-contained presentation must supply those proofs or
primary references; they are named inputs here, not newly proved claims.

Fix `0<c<beta`, put `L=log n`, `H=log(beta/c)`, and let `P_n` be the
primes in `(n^c,n^beta]`. Write `H_n=sum_{p in P_n}1/p`; input 1 gives
`H_n -> H`. Give `X_n=log p/L` probabilities `1/(p H_n)`.
Then `X_n` converges weakly to the density

    q(x)=1/(H x), c<x<beta.

Fix any `a>0`, however small, and add an independent uniform jitter
`U_n` on `[-a/L,a/L]`. Let `f_n` denote the density of `X_n+U_n`.
Its support is `[c-a/L,beta+a/L]`, it converges weakly to q, and

    f_n(x) <= M/(H x)                                  (1)

for all sufficiently large n, with `M=O(1+log(1/a))`, independent of c,beta,H. The threshold in n may depend on all fixed parameters.

Indeed the density is `L/(2a H_n)` times the sum of `1/p` over
`exp(Lx-a)<=p<=exp(Lx+a)`, intersected with the pool. For `0<a<=1/4`,
input 2 bounds the count by `C a(1+log(1/a)) exp(Lx)/(Lx)`, uniformly over the
support once n is large. The reciprocal weight is at most
`exp(-Lx+a)`, giving (1). It suffices to take `a<=1/4` in all uses.
Endpoints, and the use of closed intervals, affect only the absolute
constant. Since `f_n` integrates to one,

    integral |x| f_n(x)^2 dx <= M/H.                    (2)

The analogous bound for q is `integral x q(x)^2 dx=1/H`.

## Uniform absence of a fine lattice

There is a `kappa<1`, depending only on M,
and a finite T depending on c,beta,H,M, such that, for all sufficiently
large n,

    |hat f_n(t)| <= kappa       whenever |t|>T.         (3)

The same statement holds for q. Here `hat f(t)=integral exp(itx)f(x)dx`.

Proof: extend the envelope to `[c/2,2 beta]`. For any phase theta, the
set where `tx-theta` modulo `2pi` lies in `[-alpha,alpha]` has envelope
mass at most

    (M/H) [ (alpha/pi) log(4 beta/c) + O(1/(|t|c)) ].

To keep the constant independent H when H is small, restrict the
present application to `H>=1`, which is all that is needed. Then
`log(4 beta/c)/H<=1+log4`. The estimate follows by integrating the
bounded periodic primitive of the arc indicator minus its mean against
`1/x`; its endpoint values and total variation are `O(1/c)`.
Choose `alpha>0` an absolute sufficiently small multiple of `1/M`, and
then T sufficiently large. At most one half of the probability lies
inside this arc, uniformly in theta. Rotate `hat f_n(t)` to the positive
real axis. On at least one half of the mass its real integrand is at
most `cos alpha`; thus its modulus is at most
`1-(1-cos alpha)/2=:kappa<1`. This proves (3).

## Weighted Fourier compactness lemma

For each integer h>=1, let `f_n^{*h}` and `q^{*h}` denote h-fold
convolutions. There is an absolute C such that

    limsup_n ||f_n^{*h}-q^{*h}||_1
       <= C h sqrt(M+1) kappa^(h-1).                  (4)

Crucially C is absolute, and M,kappa do not depend on H,c,beta.
Their dependence on a is `M=O(1+log(1/a))` and
`1-kappa` bounded below by an absolute positive multiple of `1/M^2`. The frequency threshold
T does depend on the fixed window, which is harmless in this order of
limits. This avoids an unweighted L2 bound with a factor `sqrt(beta/c)`.

Proof: write `phi_n=hat f_n`, `phi=hat q`, and
`u_n=phi_n^h-phi^h`. For a Fourier transform v define the homogeneous
half-derivative seminorm

    [v]^2 = integral integral |v(s)-v(t)|^2/|s-t|^2 ds dt.

Plancherel and Tonelli give, with the same universal positive constant
C_F for all g,

    [hat g]^2 = C_F integral |x| |g(x)|^2 dx.          (5)

For example, substitute `t=s+r`, apply Plancherel in s, then use
`integral |exp(irx)-1|^2/r^2 dr = const*|x|`.
All densities here are compactly supported and L2, so these uses are
justified; the differences and convolutions are likewise L2.

Split the defining integral for `[u_n]^2` into pairs with both
`|s|>T, |t|>T` and pairs with at least one coordinate in `[-T,T]`.
On the first set, (3) and
`|z^h-w^h|<=h kappa^(h-1)|z-w|` for `|z|,|w|<=kappa` imply

    high-high contribution
      <= 2 h^2 kappa^(2h-2) ([phi_n]^2+[phi]^2)
      <= C_F 2 h^2 kappa^(2h-2) (M+1)/H.             (6)

For the remaining pairs the integral tends to zero. To see this
without a domination gap at the diagonal, fix R>T. Weak convergence
and uniformly bounded supports imply uniform convergence of phi_n and
phi_n' on every bounded interval, hence uniform C1 convergence of u_n
to zero there. On `[-R,R]^2` the integrand is bounded by
`sup_{[-R,R]}|u_n'|^2` and therefore its integral tends to zero.
For `|s|<=T, |t|>R` (and the transposed set), use `|u_n|<=2` and
integrate `16/(|t|-T)^2`. This tail is `O(T/(R-T))`, uniformly in n.
First take n to infinity, then R to infinity. This establishes the
claim about low-involved pairs. Equations (5)-(6) give

    limsup_n integral |x| |f_n^{*h}(x)-q^{*h}(x)|^2 dx
       <= 2 h^2 kappa^(2h-2) (M+1)/H.

The difference is supported in
`[h(c-a/L),h(beta+a/L)]`, a positive interval for large n. Weighted
Cauchy-Schwarz now bounds its L1 norm by the square root of the last
integral times the square root of

    integral_{h(c-a/L)}^{h(beta+a/L)} dx/x = H+o(1).

This proves (4).

## Return to actual prime products

For fixed h and desired log tolerance eta>0, choose the jitter half-width
`a<=min(1/4,eta/(2(h+1)))` above. A sum of h jittered prime logs, before
division by L, differs deterministically from its unjittered sum by
at most h a. For degrees h and h+1, the two jitter errors together are
at most `(2h+1)a<eta`.

Let `D_h(H)=TV(q^{*h},q^{*(h+1)})`. By (4) and the triangle inequality,

    limsup_n TV(f_n^{*h},f_n^{*(h+1)})
      <= D_h(H) + C (h+1) sqrt(M+1) kappa^(h-1).     (7)

Maximally couple the jittered sums: outside the TV failure probability
they are exactly equal. Disintegrate each jittered sum back to its
unjittered prime tuple. On the equality event the original log sums
differ by less than eta. Hence (7) supplies an actual-size coupling
failure bound for the iid prime-product laws, not merely exponent
convergence. Regular conditional laws exist for these real/discrete
random variables.

Conditioning h iid harmonic prime draws on being distinct changes their
joint law by at most `binom(h,2) n^-c/H_n`, which tends to zero.
For distinct tuples, forgetting order gives precisely the harmonic law
on squarefree degree-h products. Thus (7) holds for those laws too.

If the independently checked continuous comparison satisfies
`D_h(H)<=O(h log(h)/H)+O(1/h)`, first fix eta, choose h sufficiently large with
`a=min(1/4,eta/(2(h+1)))`, then H much larger
than h^2 and h log h, set `beta=epsilon/(h+1)`, and `c=beta exp(-H)`.
The smoothing error is `O(h sqrt(log(h/eta)) exp(-const*h/log(h/eta)^2))`,
which tends to zero with h for each fixed eta. The continuous
comparison tends to zero, and the reviewed full-pool energy estimate
is `G_h-1<=exp(h^2/H)-1+o(1)`. Thus eta can be arbitrarily small; h,H,c,K and the threshold in n
are then selected in that order. Finally choose fixed K with
`1/(K+1)<c`. All requirements of the existing coupling criterion then
hold simultaneously in their stated order of limits.

Status: analytic argument supplied for independent proof audit. No
novelty or final target verdict is asserted by this worker.
