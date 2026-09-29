# Prior-art and citation audit: "Total variation under largest-prime deletion"

Auditor: cold citation and bounded prior-art auditor (AI). Read-only except this file.
Manuscript: frozen packet at commit d199bfb (`paper/main.tex`, `README.md`).
Date of searches: 2026-09-28.
Searched corpus: arXiv abstract pages and PDFs (text extracted with `pdftotext` to stdout), Crossref REST metadata, DOI resolvers, publisher landing pages (IMPAN, episciences, Zenodo), Project Euclid search snippets, and general web search (US index). Five targeted precedent searches, listed in Section 5.

## Verdicts

| Axis | Verdict |
|---|---|
| Citation mechanics | PARTIAL: one must-fix (Koukoulopoulos is cited as a manuscript, but a journal version exists) |
| Attribution accuracy | PASS: every pointer checked says what the paper says; three should-fix nuances |
| Novelty qualification | PARTIAL: the paper should separate the new PNT-free proof from the statement of Theorem 1.1, which a known result may already give (see Section 3) |

## 1. Citation mechanics (checked against each source's own record)

| Bibitem | Result |
|---|---|
| Arratia | Title, author, Bolyai Soc. Math. Stud. 10, 2002, pp. 29–91 all match the arXiv 1305.0941 comments field ("appeared in Contemporary Combinatorics, 29-91, Bolyai Soc. Math. Stud., 10, Janos Bolyai Math. Soc., Budapest, 2002"). Correct. The editor and publisher are not given (optional). |
| Bergelson–Richter | Duke Math. J. 171 (2022), no. 15, 3133–3200 matches the arXiv journal-ref and the Project Euclid URL (issue-15). The DOI 10.1215/00127094-2022-0055 comes from a search snippet and is not in the bibitem (optional). The arXiv v3 link is correct (v3 dated 17 Dec 2023). |
| Kline spectrum | The Zenodo record for 10.5281/zenodo.23004980 reads: "The singular spectrum of a sparse Mertens matrix", Kline, Jeffery, v0.1.0, published 2026-09-28, resource type Software, GPL-3.0-only. It matches the bibitem. |
| Koukoulopoulos | **Must-fix.** The paper was published in Compositio Math. 149 (2013), no. 7, 1129–1149, DOI 10.1112/S0010437X12000802 (Crossref; the arXiv 1203.0596 journal-ref agrees). The cited "author manuscript, March 13, 2013" is the same text as arXiv v3 (the PDF header reads "Date: March 13, 2013"). Cite the journal version. The umontreal URL still resolves. |
| LWWY | Authors (Huixi Li, Biao Wang, Chunlin Wang, Shaoyun Yi), title, Acta Arith. 221 (2025), 117–140 all match the IMPAN landing page (DOI 10.4064/aa240909-18-6, published 2025-10-13). "no. 2" appears only in the arXiv journal-ref and is not confirmed by IMPAN or Crossref. It is plausible but unverified. The DOI could be added (optional). |
| McNamara | Hardy–Ramanujan J. 44 (2021), published online 2022-01-09, article 8924, DOI 10.46298/hrj.2022.8924. Correct. The arXiv id 2002.04007 could be added (optional). |
| Nourdin–Poly | Crossref confirms SPA 125 (2015), no. 6, 2190–2205, DOI 10.1016/j.spa.2014.12.010. Correct. arXiv id 1310.4266 (optional). |
| Richter | Crossref and the arXiv journal-ref confirm BLMS 53 (2021), no. 5, 1365–1375, DOI 10.1112/blms.12503. Citing the corrected arXiv v3 is appropriate: v3 footnote 2 says the *published* proof of Proposition 2.2 omits the restriction n_i = n'_i in (3.12), "leading to a mistake that carries through the rest of the argument." Crossref lists no corrigendum. The bibitem should say so, because the paper points readers to Prop. 2.2 and Section 3 (should-fix). |

## 2. Attribution locations

| Pointer | Says what the paper says? |
|---|---|
| Richter Prop. 2.1 | Yes. Identity (2.2): the variance of Σ_{q∈B} 1_{q\|n} equals Σ Φ(q,q')/(qq') + O(\|B\|²/N), with Φ = gcd − 1. It is stated over all n ≤ N, not over squarefree n. |
| Richter Prop. 2.2 | Yes. For k ≥ k0(η), there are equal-size finite sets B1 (primes) and B2 (products of exactly k primes), with a monotone bijection within ratio 1 ± η and log-energy ≤ η. |
| Richter Section 3 "separated logarithmic index sets" | Yes. The sets A_i ⊂ s_i ℕ with s_{i+1} > max(A_1+…+A_i) enforce property (A): distinct tuples have sums at least 2k apart. |
| Richter Lemma 3.3 (cf. for Lemma 2.3) | Yes. It has the same β(σ) = σ log σ − (σ−1) log(σ−1), for 1 < σ ≤ 16, proved through the binomial coefficient ⌊σx⌋ choose ⌊x⌋. The paper's range 1 < σ < 2 and its bound on b(e^{2a}) are its own. The second is analogous to Richter's Prop. 3.1(ii). |
| BR Prop. 2.1 | Yes. Bound (2.4): the averaging error is at most (E^log E^log Φ)^{1/2}. |
| BR Lemmas 2.2–2.3 | Yes. Primes and Ω = 2 numbers are matched by count in every ρ-adic interval, and Lemma 2.3 is the 5ε comparison. **Nuance (should-fix):** the proof of Lemma 2.2 opens with "It is a consequence of the Prime Number Theorem that…" (primes in [ρ^j, ρ^{j+1/2})). BR's matched sets therefore cannot be used in a PNT-free argument. Only Richter's construction is elementary. |
| BR Cor. 1.8 | Yes. It gives the squarefree version (1.6), with the factor 6/π². |
| LWWY Thm 1.7 | Yes. Statement (18): shift invariance of bounded a(Ω(n)) over squarefree n. |
| LWWY Thm 1.2 | Mostly. Part (1) is an Erdős–Kac × Bergelson–Richter equidistribution statement over squarefree n with p ∤ n for p ∈ S and p_max(n) ∈ T, where T is a set of primes of natural density δ(T). It is not itself a shift-invariance theorem, although it implies one for f(T^{Ω(n)}x). The phrase "also allows specified largest-prime-factor restrictions" is accurate but could be read as a shift statement (should-fix wording). |
| Arratia §§3.4–3.5, Thms 3, 5 | Yes. §3.4 covers primes and the scale-invariant Poisson process. §3.5 covers the size-biased permutation coupling. Theorem 3 bounds insertion–deletion: E Σ\|C_p − Z_p\| ≤ 2 + O((log log n)²/log n). Theorem 5 bounds log displacement to Poisson–Dirichlet: O(log log n). |
| Arratia §3.4.1 uses a PNT error estimate | Yes. It invokes (34), Σ 1/p = B + log log x + O(exp(−c√log x)), from "the error estimate for the prime number theorem". §3.6 also uses π(x) = li(x) + O(x e^{−c√log x}). |
| Nourdin–Poly Thm 1.2 | Yes. It is Prohorov's theorem as they restate it (TV convergence of normalized i.i.d. sums iff some W_{n0} has an absolutely continuous component). They reprove it in their §2.4. |
| Koukoulopoulos "elementary estimates with Fourier inversion" | Yes. The introduction says it "uses only elementary estimates and Fourier inversion". |
| McNamara, Selberg symmetry formula | Consistent with Richter's description ("deriving the PNT from (1.2)") and the abstract. The full text was not re-read. |

## 3. Central question: does a short adaptation of the cited results give Thm 1.1 or Prop. 6.3?

**(a) Direct substitution fails. Confirmed.** Remark 2.5 is correct. Richter's and BR's multiplier sets are fixed, so their prime factors survive fixed-depth deletion. LWWY's framework (Thm 1.1, "invariant average under multiplications") also does not apply to a(n) = f(T^K n). For fixed m, a(mn) = f(m·T^K(n)) for almost all n, not f(T^K n), so a is not multiplicatively invariant. LWWY Thm 1.2's p_max ∈ T condition restricts the density class of one prime and says nothing about the law of the cofactor.

**(b) BR's sets are PNT-dependent.** BR Lemma 2.2 is proved from the PNT, so it cannot serve a PNT-free route. With the PNT assumed, fine-resolution matching of primes and semiprimes is immediate.

**(c) A moving-window Richter adaptation plausibly gives the *qualitative* limit, but not the rate.** This is a sketch and an inference, not a verified proof.
- Use Richter's degrees 1 and k rather than d and d+1. Primes p > n^{1/(K+1)} give T^K(pa) = T^{K−1}(a). k-products q whose factors exceed n^{1/(K+k)} give T^{K+k−1}(qa) = T^{K−1}(a). Proposition 3.1's transfer argument then bounds TV(ν_K, ν_{K+k−1}). Doing the same with k+1 and applying the triangle inequality bounds TV(ν_{K+k−1}, ν_{K+k}). Monotonicity in depth then gives the adjacent bound. The degree mismatch is therefore not the obstacle.
- Property (A) is the obstacle. A_1 needs harmonic mass N, so max A_1 ≈ s_1 e^{N}. Then A_2 ⊂ s_2 ℕ with s_2 > max A_1 has harmonic mass about H/s_2 → 0 inside a window of log-ratio H. Separation by vastly different scales is impossible in a moving window. The paper states this correctly.
- A possible replacement: take disjoint scale blocks for the k factors, so the products are automatically distinct, and assign B1 primes fractionally subject to capacity. Thin the factor pools P_x by a factor D' so that the harmonic mass of B2 near each scale 8^z stays below the prime mass available there, about D·8^z/z. A rough count gives capacity when D'^k·C^k·k·H^{k−1} ≲ D. The energy bound in Richter's (3.12) needs D'·H/k ≫ 8^{6k}/D, and the B1 energy needs harmonic mass ≫ 1. These conditions appear compatible once H ≥ exp(C k²) or so. Richter's Lemma 3.5 supplies the resolution η (k ≥ 2/ε⁴, with 8^{2ε} ≤ 1 + η). All of these inputs are Chebyshev-level; no Fourier step is needed.
- Cost: k ~ τ^{−4} and H ~ exp(C k²) mean K must be about exp(exp(C τ^{−8})). That rate is iterated-logarithmic, far weaker than (log K)^{−1/4}, and it does not give Prop. 6.3's uniformity in H.
- Assessment: the qualitative "In particular" of Theorem 1.1 may follow from a multi-page Richter adaptation. I found no written instance of one, and I have not checked the capacity and energy bookkeeping. The quantitative bound (eq:main) and Prop. 6.3 (H-uniform coupling at fixed resolution, without the PNT) are not given by this route.

**(d) With the PNT, the statement of Theorem 1.1 is plausibly routine.** This is an inference. Conditional on the K deleted primes, the remaining m is uniform among squarefree m ≤ n/Q with P^+(m) < q_K. So ν_{n,K}(m) = #{r ≤ n/m squarefree, ω(r) = K, P^-(r) > P^+(m)}/Q(n). With the PNT, standard Buchstab-type asymptotics for integers with exactly K prime factors all > y would identify lim_n TV(ν_{n,K}, ν_{n,K+1}) as an explicit integral of |ω_K(u) − ω_{K+1}(u)|. Heuristically, K behaves like a Poisson count with mean ≈ log u, and typical u ≈ e^K, which suggests a rate of order K^{−1/2}, better than (log K)^{−1/4}. The novel content is therefore the PNT-free derivation (Props. 3.1 and 6.3 with Lemma 6.2), not the distributional statement alone. The paper currently says "The specific result put forward is Theorem 1.1" without this qualification.

**(e) Prop. 6.3 with the PNT is immediate.** Primes are equidistributed at fixed multiplicative resolution, and Lemma 5.1 then applies directly. Without the PNT, none of the cited works gives an H-uniform fixed-resolution coupling. Nourdin–Poly/Prohorov concern a fixed summand law, and Richter's Lemma 3.5 gets resolution combinatorially, but only with k ≫ η^{−4} and without H-uniformity. I found no precedent for the weighted-Plancherel estimate. Unresolved beyond the bounded corpus.

## 4. Conclusions, separated

**(i) Exact prior art that must be credited:**
- Richter (gcd-energy averaging, the prime vs k-product matching, the Lemma 3.3 interval bound). Credited.
- Bergelson–Richter (averaging principle, matched intervals, squarefree Cor. 1.8). Credited.
- LWWY (squarefree shift invariance). Credited.
- Credit is missing for the Daboussi (1975, Lemma 1) and Kátai (1986, Eq. 3.1) origin of the divisor-averaging criterion. Richter and BR both attribute it this way (should-fix).

**(ii) Routine consequences of known results (inferences):**
- Theorem 1.1's statement, and likely a better rate, given the PNT (Section 3d).
- Prop. 6.3 given the PNT.
- Plausibly the qualitative limit of Thm 1.1 by a Richter moving-window adaptation (Section 3c; unverified).
- Corollary 1.2 (M(n) = o(n)) is classical and is not claimed as new. That is correct.

**(iii) Unresolved comparisons:**
- Whether a PNT-conditional computation of lim_n TV(ν_K, ν_{K+1}) exists in the anatomy-of-integers literature (Knuth–Trabb Pardo on k-th largest prime factors; Tenenbaum's texts). Not accessed.
- D. Chen, "Rigidity of averages over the two largest prime factors", arXiv:2608.05191 (Aug 2026). Abstract only: convergence of averages of f(P_1(n)) forces convergence of those of f(P_2(n)) to the same limit, via Dickman kernels and Wiener's Tauberian theorem. This is an adjacent-depth comparison at K = 0 for functions of the largest remaining prime, with no TV and no PNT-free claim. It is related but not a precedent; optional mention.
- Whether the Section 3c adaptation closes.

## 5. Targeted precedent searches (five)

1. "removing largest prime factors random integer distribution of remaining part n/P(n) iterated total variation limit". Found Arratia; Sun, arXiv:2609.11735 (tilted Billingsley model, cofactor law in TV under a P^+-dependent Gibbs weight; different model, no deletion depth); Chen, arXiv:2608.05191.
2. Daboussi's elementary PNT. The original C. R. Acad. Sci. Paris 298 (1984) note was **not accessed**. An accessible exposition exists: G. Tenenbaum, "Convolutions et équations fonctionnelles : sur la preuve élémentaire de Daboussi", in *Trois conférences…*, Journées État de la Recherche, Bordeaux, Dec 2000 (tenenb.perso.math.cnrs.fr/PPP/JER.pdf). I read §3. Daboussi's argument writes n = ab with a y-smooth and b y-rough, uses M(x) = Σ_b μ(b) M(x/b, y) for fixed y, and bounds limsup|M(x)|/x by ∏_{p≤y}(1−1/p) ∫ |M(t,y)|/t² dt. It removes all large primes at a fixed threshold y. It is not a deletion-depth or TV statement, and it has no moving-window multipliers. It matters only as a conceptual ancestor, since the smooth part plays the role of the remaining integer. An optional sentence would suffice. Not inspecting the original is not a gap for the paper's claims.
3. "Richter … largest prime factor removed … invariance arXiv 2025 2026". No direct precedent. Loyd, Wang, and LWWY-type P^+ restrictions only.
4. "iterated removal of largest prime factor limit law … squarefree … TV distance of cofactor". Nothing beyond items 1–3.
5. Kátai and Daboussi–Kátai: covered through the Richter and BR citations of [Dab75, Lemma 1] and [Kát86, Eq. (3.1)]. The originals were not accessed.

**Not accessed (not counted as negative evidence):**
- Daboussi 1975 and 1984 (originals); Kátai 1986.
- The published BLMS text (HTTP 403); the published Duke and Acta Arith. PDFs (arXiv versions read); the Compositio PDF (Crossref metadata plus the author manuscript read); the Bolyai volume.
- Tenenbaum–Mendès France, ch. 4; Knuth–Trabb Pardo 1976.
- Chen 2608.05191 and Sun 2609.11735 (abstracts only); McNamara's full text.

## 6. Findings

| id | severity | location | finding | exact suggested replacement text (must-fix) |
|---|---|---|---|---|
| F1 | must-fix | bib `Koukoulopoulos` | The journal version exists: Compositio Math. 149 (2013), no. 7, 1129–1149. The manuscript cited is arXiv v3. | `D. Koukoulopoulos, \emph{Pretentious multiplicative functions and the prime number theorem for arithmetic progressions}, Compositio Mathematica \textbf{149} (2013), no.~7, 1129--1149. \url{https://doi.org/10.1112/S0010437X12000802}. Author version: \url{https://arxiv.org/abs/1203.0596}.` |
| F2 | must-fix | §1.1 last paragraph; README "What is new" | The paper presents Theorem 1.1 as "the specific result put forward". Because the PNT is known, the statement is plausibly derivable from it by standard anatomy estimates, possibly with a better rate (§3d). The novelty lies in the PNT-free proof and in Prop. 6.3. | In main.tex replace "The specific result put forward is Theorem~\ref{thm:main}, with M\"obius cancellation as its arithmetic consequence." with: "The specific result put forward is a proof of Theorem~\ref{thm:main} that does not assume the prime number theorem, with M\"obius cancellation as its arithmetic consequence. Since the prime number theorem is known, the statement of Theorem~\ref{thm:main} alone is not claimed as new: assuming it, the law of the remaining integer given the deleted primes is explicit, and standard asymptotics for integers with a prescribed number of large prime factors may identify $\lim_{n}\TV(\nu_{n,K},\nu_{n,K+1})$, possibly with a better rate in $K$. We have not carried out that comparison." In README replace "The paper puts forward two things: the deletion theorem above, for the full distribution of the remaining integer, and the uniform matching estimate" with "The paper puts forward two things: a proof of the deletion theorem above that does not assume the prime number theorem, and the uniform matching estimate", and add after that paragraph: "The statement of the deletion theorem alone is not claimed as new; it may follow from the prime number theorem by standard methods." |
| F3 | should-fix | §1.1 para 3, after "…not every possible adaptation of that construction." | A moving-window Richter variant (disjoint scale blocks, thinned pools, capacity assignment, degrees 1 vs k and 1 vs k+1) may give the qualitative limit without Fourier analysis, at an iterated-log rate. Say so, so the rate and H-uniformity are clearly the contribution. | Suggested: "A moving-window variant of that construction, with thinned prime pools in place of separated index sets, might give the qualitative limit in Theorem~\ref{thm:main} without Fourier analysis, but with parameters growing much faster; we have not checked it, and it would not give the rate in \eqref{eq:main} or the uniformity in Proposition~\ref{prop:matching}." |
| F4 | should-fix | §1.1 para 1 (BR sentence) | BR's proof of Lemma 2.2 assumes the PNT. That is relevant to a PNT-free paper and it strengthens the paper's reliance on Richter. | Append: "Their proof of Lemma~2.2 uses the prime number theorem, so those sets are not available to an argument that does not assume it." |
| F5 | should-fix | §1.1 para 2 (LWWY Thm 1.2) | Theorem 1.2(1) is an equidistribution / Erdős–Kac statement with a p_max(n) ∈ T condition (T of natural density), not a shift-invariance theorem. | Replace "Their Theorem~1.2 also allows specified largest-prime-factor restrictions." with "Their Theorem~1.2(1) proves an equidistribution statement of this kind over squarefree integers whose largest prime factor lies in a prescribed set of primes of natural density." |
| F6 | should-fix | bib `Richter` | The published proof of Prop. 2.2 has an error, corrected only in arXiv v3 (footnote 2), and Crossref lists no corrigendum. The paper's pointers to Prop. 2.2 and §3 should be read in v3. | Append to bibitem: "The published proof of Proposition~2.2 contains an error corrected in this version (footnote~2); references here are to this version." |
| F7 | should-fix | §1.1 para 1 "We use this established averaging principle." | Richter and BR both trace the criterion to Daboussi [Dab75, Lemma 1] and Kátai [Kát86, Eq. (3.1)] via the dual Turán–Kubilius inequality. | Suggested: "...averaging principle, which Richter and Bergelson--Richter trace to Daboussi and K\'atai." Add the two bibitems: H. Daboussi, Fonctions multiplicatives presque périodiques B, Astérisque 24–25 (1975), 321–324; I. Kátai, A remark on a theorem of H. Daboussi, Acta Math. Hungar. 47 (1986), 223–225, doi:10.1007/BF01949145. These details are copied from Richter's bibliography and were not independently verified. |
| F8 | optional | bib BR, LWWY, Richter, NP, McNamara | Add DOIs and arXiv ids: BR 10.1215/00127094-2022-0055 (from a search snippet); Richter 10.1112/blms.12503; LWWY 10.4064/aa240909-18-6; NP arXiv:1310.4266; McNamara arXiv:2002.04007. "no. 2" for LWWY is unconfirmed by the publisher. | n/a |
| F9 | optional | bib Arratia | Add the editor and publisher (János Bolyai Mathematical Society, Budapest). | n/a |
| F10 | optional | §1.1 para 5 | Consider citing Prohorov's original theorem directly alongside Nourdin–Poly's restatement. | n/a |
| F11 | optional | §1.1 | Recent related work: Chen, arXiv:2608.05191 (adjacent largest vs second-largest prime averages, Tauberian); Daboussi's smooth/rough decomposition (Tenenbaum 2000 exposition). Neither is a precedent; either could get a one-line mention. | n/a |

No finding challenges the correctness of any cited pointer. The must-fix items are one bibliographic update (F1) and one scoping sentence about what is new (F2).
