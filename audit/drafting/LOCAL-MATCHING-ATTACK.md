# Adjacent loguniform product-size laws: a uniform TV bound

2026-09-28. Independent local matching worker. No source retrievals,
no numerical workload, no new agents. This note proves the continuous
comparison needed by the proposed prime-log smoothing route. It does
not establish that smoothing route or the original prime-product match.

## Continuous theorem

Let 0<c<beta, H=log(beta/c), and let X_i be independent with density

    q(x)=1/(H x),  c<=x<=beta.

Put S_h=X_1+...+X_h and M_h=max(X_1,...,X_h). Total variation is
supremum over measurable sets, equivalently one half of the L1 density
difference. For every integer h>=1,

    TV(Law(S_h),Law(M_h)) <= h log(h)/H.

The right side is zero when h=1. Consequently, for d>=1,

    TV(Law(S_d),Law(S_(d+1)))
      <= [d log d+(d+1)log(d+1)]/H
         + d^d/(d+1)^(d+1).

In particular the adjacent sum laws approach each other in TV whenever
d tends to infinity and H/(d log d) tends to infinity. The energy regime
H>>d^2 is more than sufficient. The bound is invariant under scaling
c,beta by the same factor.

## Proof of sum versus maximum

For h>=2, condition on the lower h-1 order statistics of the sample.
Write v for their maximum and A for their sum; thus A<=(h-1)v.
Conditionally, the top order statistic X has density

    1/[x log(beta/v)], v<=x<=beta.

The conditional sum is X+A and the conditional maximum is X. Compare
the densities of X+A and X. On their common support, the translated
density is 1/[(x-A)log(beta/v)], which is at least the original density
1/[x log(beta/v)]. Therefore their total variation is exactly the
original probability mass in the bottom, uncovered interval:

    TV(Law(X+A),Law(X))
      = min{1, log(1+A/v)/log(beta/v)}
      <= log(h)/log(beta/v).

This argument also covers v+A>=beta, where the supports are disjoint
up to null sets. Mixture convexity of total variation now gives the
expectation of the last upper bound.

The variables log(X_i/c)/H are independent uniform variables on [0,1].
Thus Y=log(v/c)/H, the second largest of h uniforms, has density

    h(h-1)y^(h-2)(1-y), 0<y<1.

Since log(beta/v)=H(1-Y), integration gives

    E[1/log(beta/v)]
      = h(h-1)/H * integral_0^1 y^(h-2) dy
      = h/H.

This proves the first bound. This is an L1/TV argument, not a bound on
CDF distance or merely a relative-size coupling.

## Adjacent maximum laws

Under the increasing transformation x -> log(x/c)/H, M_d and M_(d+1)
have densities d t^(d-1) and (d+1)t^d on [0,1]. These densities cross
once, at t=d/(d+1). Their total variation therefore equals

    max_(0<=t<=1) [t^d-t^(d+1)]
      = d^d/(d+1)^(d+1)
      <= 1/(d+1).

Apply the triangle inequality through M_d and M_(d+1) to obtain the
displayed adjacent-sum estimate.

## Useful energy fact for optional reweighting

Let pi be a probability law on squarefree multipliers, and let pi'
be another probability law with pi'(b)<=M pi(b) pointwise. Define
G(pi)=E[gcd(B,C)] for independent B,C with law pi. Then

    G(pi')-1 <= M^2 [G(pi)-1].

Indeed gcd(b,c)-1 is nonnegative, so apply the pointwise domination
directly to its double sum. In particular, conditioning a full pool on
an event of probability q costs at most q^(-2) in excess energy. This
preserves the exact baseline 1; the weaker bound G(pi')<=M^2 G(pi)
would not suffice. Nothing here asserts an adequate conditioning event
or weighted prime construction exists.

## Remaining obligation and a failed estimate to avoid

Actual log primes have an atomic law whose convolution powers at
adjacent degrees have disjoint supports by unique factorization.
Smoothing at fixed log radius eta is therefore essential. The theorem
above supplies the continuous comparison only. To use it, prove that
smoothed harmonic prime-log convolution powers are close in TV to
suitable smoothing of the continuous laws, with error tending to zero
as d grows uniformly for H>>d^2.

An ordinary unweighted L2 argument using the whole support length and
a pointwise density bound loses a factor roughly sqrt(beta/c)=exp(H/2).
Combining that loss with a fixed spectral contraction q^d cannot reach
H>>d^2. It is not a mathematical obstruction; it is a defect of that
estimate. A proposed weighted Fourier repair is under independent
investigation by the other worker and coordinator.

Elementary reciprocal-prime Mertens CDF error O(1/log n) alone is also
insufficient: after restoring actual logs it can leave O(1) displacement,
and CDF/Kolmogorov control does not provide Prokhorov control on arbitrary
unions of narrow intervals. No PNT input is used in this note.
