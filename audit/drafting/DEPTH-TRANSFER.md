# Neighboring-depth transfer: coordinator synthesis

2026-09-28. Conditional derivation, INTERNAL-NONINDEPENDENT review only.
The proposed positive-count estimate is UNPROVED and novelty UNRESOLVED.

Let C_k(n,j) count descendants of nonroot j at exactly k edges below j.
For k>=1, sum_{j>1} C_k(n,j)<=n, since a squarefree integer has at most
one ancestor k steps above it. The damped recurrence gives exactly

    g_j-1 = sum_{k>=1} (-alpha)^k C_k(n,j).

Pair odd and even terms and use positive-part subadditivity. With

    D_l(n)=sum_{j>1} (C_{2l}(n,j)-C_{2l-1}(n,j))_+,

one obtains

    P_alpha(n) <= sum_{l>=1} alpha^(2l-1) D_l(n).

This uses (alpha b-a)_+ <= (b-a)_+ for a,b>=0 and alpha<1.
Each D_l(n)<=n. Consequently, if

    d_l=limsup_{n->infinity} D_l(n)/n ->0 as l->infinity,

then the target follows. For fixed alpha the summable geometric bound
permits limsup through the sum as an upper bound. Next split the sum
at a fixed l=K; the finite initial contribution times 1-alpha vanishes
as alpha approaches1, and the tail is bounded by sup_{l>K}d_l times
(1-alpha)*alpha/(1-alpha^2), which is at most sup d_l. Let K grow.

Thus a sufficient bridge is overlap between neighboring-depth ancestor
distributions, stated solely with positive counts. For each fixed k,
sum C_k/n tends to 6/pi^2 by the elementary squarefree density and the
elementary zero density of integers with bounded omega. Both adjacent
levels therefore have the same limiting total mass. D_l measures the
part of one level not matched pointwise by the preceding level.

The finite-clique obstruction shows that arbitrary ordered forests can
have D_l/N tending to1 for every fixed l, so the new condition does not
evade that obstruction by notation. The integer multiplicative scale
must supply actual overlap. Heuristic analogy: many successive prime
deletions may spread the distribution of the logarithmic size enough
that one extra deletion changes little. Coarse distributional convergence
would NOT imply this coordinatewise total-variation estimate. That gap
is essential; no transfer from a Dickman law is assumed.

## Finite test charter (within EXCURSION-CHARTER budget)

Three n: 10000,100000,1000000. Exact integer counts. At most30 CPU-sec,
256MiB working arrays (procedural), one CPU, owning .venv interpreter.
Report both unmatched mass D_l/n and total mass at both depths. No
asymptotic conclusion when deep levels are nearly empty. No new agents,
no source requests. Success means checked finite counts only.

## Fixed-prime core lemma

For any fixed y and fixed alpha<1, the total positive excursions at
squarefree j with P+(j)<=y are o(n). There are finitely many such j,
all divisors of the product of primes<=y. For each fixed j the explicit
descendant expansion is bounded in absolute value by
sum_{d<=n/j} alpha^omega(d)=o(n), using the reviewed finite-prime sieve.
Thus the unresolved excursions must involve prime thresholds increasing
with n. This is a routine consequence of the checked sieve lemma, not
evidence that the whole tail is controlled.
