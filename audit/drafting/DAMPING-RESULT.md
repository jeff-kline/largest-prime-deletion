# Damping reduces the question to interior absolute mass

2026-09-28. Local derivation and internal, nonindependent review only.
No paper or release files changed. Novelty remains unresolved.

## Exact construction and certificate

For 0<alpha<1 set g_1=0 and, descending through the forest,

    g_j = 1 - alpha sum_{parent(i)=j} g_i       (j>1).

Only squarefree i>1 have a parent, i/P+(i). Nonsquarefree vertices
are isolated. This construction needs prime factors and squarefreeness,
but no Mobius values. It is a damped alternating path expansion; that
description does not itself remove the arithmetic difficulty.

Let r=A^T g-u, with u=(0,1,...,1). Then

    r_1 = sum_{p prime <=n} g_p,
    r_j = (1-alpha)/alpha * (1-g_j), j>1.

The exact dual identity is mu^T r=1-M(n), hence

    |M(n)-1| <= |r_1| + (1-alpha)/alpha * sum_{j>1}|1-g_j|.

## The root is sublinear at each fixed damping parameter

Define F_alpha(n)=sum_{m<=n, m squarefree} (-alpha)^omega(m),
including m=1, and omega(m) the number of distinct prime factors.
The unique path from a squarefree m to 1 has length omega(m), so

    r_1 = (1-F_alpha(n))/alpha.

For fixed alpha<1, F_alpha(n)=o(n) without PNT. Indeed

    |F_alpha(n)| <= sum_{m<=n} alpha^omega(m).

For any fixed finite set of primes p<=z, the latter mean has limsup
at most product_{p<=z}(1-(1-alpha)/p), by counting residue classes
modulo the product of those primes. This product tends to zero by
Euler's elementary divergence of sum_p 1/p. First take n to infinity
with z fixed, then z to infinity. No varying-alpha uniformity follows.

## Exact remaining target

Put H_n(alpha)=n^{-1}sum_{j>1}|1-g_j|. A sufficient condition is

    lim_{alpha up to 1} (1-alpha) limsup_{n to infinity} H_n(alpha)=0.

The order of limits is essential. For each fixed alpha the root term
vanishes first. A uniform bound limsup H_n(alpha)<=C, for alpha>=1/2,
would be more than sufficient, but is UNPROVED here.

The immediate absolute path count gives only
H_n(alpha)<=alpha/(1-alpha), which fails exactly at the needed limit.
Thus damping has not proved PNT: improving this bound is load-bearing.

There is a further exact localization. Let Q(n) count squarefree m<=n
and P_alpha(n)=sum_{j>1}max(g_j-1,0). Summing the finite geometric
series along all squarefree paths yields

    sum_{j>1}g_j = n-Q(n)+(Q(n)-F_alpha(n))/(1+alpha),
    n H_n(alpha) = (alpha Q(n)+F_alpha(n))/(1+alpha)-1+2P_alpha(n).

Therefore the obstruction is excessive POSITIVE excursions of g_j
above its leaf value 1. A uniform O(n) upper bound on their total,
or the weaker vanishing condition with factor 1-alpha, would suffice.
This is the proposed target for a Selberg logarithmic correction or
elementary inequality; no such bound has been established in this note.

## Bounded computation

Five sizes from 1000 to 1000000 and five parameter choices, per
RESIDUAL-CHARTER.md. Runtime 7.16 seconds, one CPU, stdlib only.
All 25 dual checks passed tolerance; alpha=1 exact controls passed
integer-valued equality. Floating-point diagnostics are not interval
certificates or asymptotic evidence.

At alpha=0.9, H_n(alpha) was:

| n | H_n(0.9) |
|---:|---:|
| 1000 | 0.284454 |
| 10000 | 0.285726 |
| 100000 | 0.287027 |
| 300000 | 0.287660 |
| 1000000 | 0.287574 |

For alpha=1-1/log(n), the total l1 residual divided by n decreased
from 0.05698 to 0.02329 across the endpoints, while squared-l2/n
increased from 0.2513 to 1.1982 (not monotonically). This favors
investigating the l1 certificate first; it proves no limiting behavior.

The alpha=1 control is exactly the original Mertens problem. Choosing
alpha extremely close to 1 without a uniform theorem cannot remove it.

## Recommended resources and next action

One analytic worker on the uniform interior bound, one computational
worker on positive-excursion structure, and a cold reviewer once the
first inequality is proposed. No new agents were launched in this test.
A laptop and existing isolated environment suffice; no GPU or cluster.

Primary reading: Selberg 1949 elementary PNT, Levinson 1969 motivated
account (especially smoothing), with Richter 2021 as an independent
comparison for multiplicative averaging. Classical PNT is the external
baseline; a new proof requires a new argument, not a change of notation.

Next action: attack the positive-excursion bound before enlarging the
numerical range. Either prove a uniform estimate or identify an explicit
arithmetic subfamily forcing the current bound to diverge too quickly.
