# Exact-prefix coupling: a quantitative reduction

2026-09-28. Construction worker. Main neighboring-depth limit OPEN.
The reduction below is proved by elementary counting; the required moving
multiplier sets are NOT constructed. No source requests or experiments.

## A moving-multiplier criterion

Write `Q(x)` for the number of squarefree positive integers at most `x`,
and `U_x` for their uniform law. Fix integers `K >= d+1`, and `epsilon<1/2`.
Let `B_d(n)` and `B_{d+1}(n)` consist of squarefree integers of exactly the
indicated number of prime factors. Give their members nonnegative weights
`w_b`. Require every prime factor of every multiplier to exceed
`L=n^(1/(K+1))`, and every multiplier to be at most `R=n^epsilon`.
The sets and weights may depend on `n`.

For either set put

    H = sum_b w_b/b,
    h(b) = w_b/(b H),
    G = H^(-2) sum_{b,c} w_b w_c gcd(b,c)/(bc).

Assume `H>0` and bounded `G` as `n` increases. Suppose a coupling of the
two probability laws `h_d,h_{d+1}` satisfies

    Pr(max(b/c,c/b)>1+eta) <= rho.

Then, for fixed `K,d,epsilon,eta`,

    TV(nu_n,K,nu_n,K+1)
      <= (sqrt(G_d-1)+sqrt(G_{d+1}-1))/2
         + rho + C eta + o_n(1).

The absolute constant `C` can be chosen uniformly for `0<=eta<=1`.
If the energies depend on `n`, take limsups on the right. Thus sets
available along arbitrarily large `K` with both energies tending to 1,
`eta` tending to zero, and `rho` tending to zero prove the target:
TV contracts under each application of the deterministic map `T`, so a
subsequence of depths suffices. The criterion requires matching actual
multiplier sizes within a ratio tending to 1; matching only exponents
`log b/log n` is insufficient.

### Proof

For squarefree `m<=n`, define `D(m)=sum_{b|m} w_b`. Its size-biased law
has total-variation distance from `U_n` at most

    (1/2) sqrt( E[D^2]/E[D]^2 - 1 ).

Elementary squarefree counting, uniformly for a squarefree integer `l`,
gives

    #{m<=n: m squarefree, l|m}
      = (6/pi^2) n / product_{p|l}(p+1)
        + O(2^omega(l) sqrt(n/l)).

For completeness, count `m=l a` with `(a,l)=1` and squarefree `a`;
expand the squarefree indicator with `sum_{r^2|a} mu(r)` and count
integers coprime to `l` by inclusion-exclusion. The floor errors are at
most `2^omega(l) sqrt(n/l)` and the convergent-series tail is bounded
by the same expression.

For first and second moments, `l=b` and `l=lcm(b,c)` respectively.
Replacing `product(p+1)` by `l` has relative error `O_K(1/L)`.
The first-moment relative counting error is
`O_K(sqrt(R/n))`. For the second moment, use

    1/sqrt(lcm(b,c)) <= sqrt(R)/sqrt(bc),
    sum_b w_b/sqrt(b) <= sqrt(R) H.

This bound alone gives `O_K(R^(3/2)/sqrt(n))`, which would unnecessarily
restrict epsilon to below 1/3. A sharper bound uses

    1/sqrt(lcm(b,c))
       <= R / lcm(b,c),

since `lcm(b,c)<=R^2`. Therefore the second-moment error relative to
`H^2` is `O_K(R G/sqrt(n))=o(1)` for `epsilon<1/2`.
Consequently `E[D]/H=1+o(1)` and `E[D^2]/H^2=G+o(1)`.

Generate the size-biased law by choosing a pair `(b,a)` with weight
`w_b`, where `a<=n/b` is squarefree and coprime to `b`. The marginal
law of `b` differs by `o(1)` in TV from `h(b)`. Indeed, uniformly in `b`,
the number of eligible `a` is

    (6/pi^2)(n/b)(1+O_K(1/L)+O_K(sqrt(R/n))).

Removing the coprimality restriction changes each conditional law of
`a` by `O_K(1/L)`: a union bound over `p|b` uses
`Pr_{U_x}(p|a)<=C/p` for `x=n/b>=n/R`.

Every prime factor of `b` is among the first `K` factors deleted from
`ba`. Otherwise `ba` would contain at least `K+1` primes exceeding
`n^(1/(K+1))`, contradicting `ba<=n`. Hence exactly, including cases
where deletion reaches 1,

    T^K(ba)=T^(K-d)(a).

For a multiplier `c` with `d+1` factors the corresponding identity is

    T^(K+1)(ca)=T^(K-d)(a).

After removing the negligible coprimality restrictions, both sides
therefore apply the same map to `U_{n/b}` and `U_{n/c}`. On good coupled
pairs their TV distance is at most `C eta+o(1)`, because these uniform
laws are nested and `Q(x)=(6/pi^2)x+O(sqrt(x))`, uniformly for
`x>=n/R`. On bad pairs use the bound 1. Triangle inequality proves the
criterion.

## What the criterion does and does not repair

For an unweighted prime set, exactly

    G-1 = H^(-2) sum_p (p-1)/p^2 <= 1/H.

Thus a moving prime window with diverging harmonic mass has the required
divisor-count concentration. A fixed finite template cannot supply it.
The moving threshold avoids the earlier fixed-template problem and makes
the exact-prefix identity automatic.

Replacing a whole prime window by all semiprimes from that same window
does not automatically provide size matching. In a model with harmonic
prime exponent density `dt/(t log(beta/alpha))` on `[alpha,beta]`, put
`t0=sqrt(alpha beta)`. A prime exponent is at most `t0` with probability
1/2. A sum of two independent such exponents is at most `t0` with
probability at most 1/4. This gives a product-size CDF discrepancy of
at least 1/4. The calculation is an exact obstruction for that model,
not an unconditional theorem about short multiplicative prime bins.

A concrete repair is to compare degree `d` with degree `d+1`, for growing
`d`, using tailored multiplier subsets or weights. The criterion above
states exactly what must be preserved: energy close to 1 and actual-size
coupling close to the diagonal. Concentration alone does not prove size
matching; limiting exponent distributions do not prove it either.

Status: quantitative reduction PROVED, awaiting independent review;
construction of the required moving multiplier sets OPEN.

## Energy bound for full fixed-degree product pools

The coordinator suggested full product pools. Their energy admits the
following finite bound, without any prime-distribution assumption.
Let `P` be a finite set of primes, `H=sum_{p in P}1/p`,
`delta=max_{p in P}1/p`, and let `B_d` contain all products of `d`
distinct primes from `P`, with unit weights. If

    theta = binom(d,2) delta/H < 1,

then its normalized gcd energy satisfies

    G_d - 1 <= (exp(d^2/H)-1)/(1-theta)^2.

Proof: writing `e_j` for elementary symmetric functions of the numbers
`1/p`, independent draws with probabilities `1/(pH)` collide with
probability at most `binom(d,2) delta/H`. Thus

    e_d >= H^d (1-theta)/d!,  and  e_j <= H^j/j!.

For an `r`-element subset `S` of primes, the harmonic probability that a
random `b in B_d` contains `S` is at most

    (1-theta)^(-1) (d)_r H^(-r) product_{p in S}1/p.

Use `gcd(b,c)=sum_{s|gcd(b,c)} phi(s)` for two independent harmonic
draws. The empty subset contributes exactly 1. For subsets of size `r`,
the remaining contribution is at most

    (1-theta)^(-2) (d)_r^2 H^(-2r)
      * e_r( (p-1)/p^2 : p in P )
    <= (1-theta)^(-2) (d^2/H)^r/r!.

Sum over `1<=r<=d` and enlarge to the exponential series. This proves
the bound. Consequently `H>>d^2` supplies both adjacent-degree energy
requirements, provided the factor threshold and product upper bound
also hold. Actual-size coupling remains the sole missing input for
this full-product candidate; the energy statement itself does not
provide such coupling.
