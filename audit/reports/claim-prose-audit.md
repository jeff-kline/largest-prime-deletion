# Claim and prose audit, packet d199bfb

Verdict: **PARTIAL**. No claim inconsistency and no wrong cross-reference. Blockers are reader-facing prose defects in the README and a missing prior-art credit.

## Verified consistent (checked by reading README.md, main.tex, pdftotext of main.pdf, pdfinfo)

- Title "Total variation under largest-prime deletion", author Jeffery Kline, Version 0.1.0 "release candidate": identical in README:1-5, PDF title page, main.tex:5,20-22, pdfinfo (Title, Author, Subject).
- Date: PDF title page and main.tex say September 28, 2026. pdfinfo CreationDate is Sep 27 19:00 CDT, which is Sep 28 00:00 UTC (fixed SOURCE_DATE_EPOCH), so it agrees in UTC. README carries no date.
- Principal claim, quantifier order (n-limit first, K fixed, then K to infinity) and limits agree across abstract, Section 1 (Thm 1.1, closing paragraph) and README:25-29, 47-50, 95-97.
- README cross-references match the PDF: Section 1.1, Remark 2.5, Proposition 6.3, Lemmas 5.1 and 6.2.
- README does not call the proof strictly elementary (README:49-50; paper Section 9) and disclaims a new Mertens/PNT error term (README:47-49; abstract).
- README leads with the full remaining-integer distribution and depth bound. The uniform matching estimate is named as the technical contribution (README:54-57) and M(n)=o(n) as a consequence.
- Novelty is qualified to a bounded, targeted reading (README:81-85; paper 1.1 last paragraph).
- Squarefree and TV are defined before use in README (squarefree at README:15-16; TV at README:28, one line after its first use in the display).

## Findings

| id | class | file:line | finding | exact replacement sentence (must-fix only) |
|---|---|---|---|---|
| C1 | must-fix | README.md:37-40 | mu is used and Möbius is named without definition. A newcomer cannot read M(n). The paper defines mu at main.tex:70. | "Testing against the Möbius function (μ(m) is 0 if m has a repeated prime factor, and otherwise is +1 or −1 as m has an even or odd number of prime factors) then gives" |
| C2 | must-fix | README.md:33-35 | "d and d + 1 such primes" uses d, which is undefined, and "reciprocal-weighted" is never explained. "Windows of primes that move with n" (README:32) is also undefined. | "A weighted Fourier estimate matches two random products, one of d primes and one of d + 1 primes, where each prime p from a window {p : n^c < p ≤ n^β} is drawn with probability proportional to 1/p (the reciprocal weight), so that the logarithms of the two products nearly agree, with constants that do not depend on the logarithmic width of the window." |
| C3 | must-fix | README.md:21-22 | "stops changing in distribution" overstates the result. The theorem gives only a bound on the change in distribution, taken as limsup in n. It is not eventual constancy. Standard: result not stated more strongly than the argument. | "The paper proves that the distribution of the remaining integer changes less and less as the depth K grows, in the following sense." |
| C4 | must-fix | README.md:59-75 (and main.tex:92, main.tex:548) | Two items on the required do-not-claim-as-new list are not credited as established in either README or paper 1.1. (a) Testing a signed function against the parity shift, mu(T^{K+1}m) = -mu(T^K m), is the standard parity-of-omega argument. (b) Plancherel and the fractional seminorm identity are credited as standard only inside the paper, at Section 1.1 lines about Lemma 6.2, and not in the README. | Add to the README list: "- **Parity testing and the Fourier identity**: reading M(n) off the sign change of μ under one more deletion, and the Plancherel and fractional-seminorm identity in Lemma 6.2, are standard tools and are not claimed as new." For the paper, add the parity sentence to the last paragraph of Section 1.1. |
| C5 | must-fix | README.md:92 | "process-separated AI audits" is process-history jargon, and a newcomer cannot tell what it means. Model agreement must not read as validation. Lines 93-94 handle that part correctly. | "The proof was checked by several fresh-context AI audits; their reports are in `audit/`." |
| C6 | optional | README.md:31-37 | The paragraph is dense for a newcomer: "multiplier-comparison method", "coupling", "exact deletion identity", "greatest-common-divisor bound" are undefined. The intro is the abstract's sentence order and stays faithful to it. If C2 is applied, one plain sentence would help. | none required |
| C7 | optional | README.md:25-29 | The README omits "for all sufficiently large K" (Thm 1.1). Covered by "as K → ∞", so not wrong. TV is used in the display before its definition on the next lines. | none required |
| C8 | optional | README.md:28 | "controls every bounded test at once" is true up to a factor of 2 (main.tex eq. 1: |E_P f − E_Q f| ≤ 2 TV for |f| ≤ 1). | none required |
| C9 | optional | README.md:5, main.tex:22, PDF metadata | "release candidate / no tag or DOI" is correct for this packet. At release, update README:5, main.tex date/version line and pdfsubject together (release-time item, not a defect now). Add a date to the README status line so it matches the PDF. CITATION.cff, VERIFICATION.md and CORRECTIONS.md were not in the packet and were not checked. | none required |
| C10 | optional | main.pdf (whole) | The paper has no AI-role sentence. The program standard makes AI the stated default, and the README has "Role of AI" (README:120-124), so this is acceptable. The README disclosure does not present model agreement as validation. | none required |

## Checked and clean

- No "external pass", "agent lane", "another model found", "quarantined" or "working draft" in README or main.tex.
- No broad historical or encyclopedia opening in README.
- No claim of a new quantitative error term; the paper says so explicitly (Section 9, main.tex:568).
- Prior art for gcd averaging, squarefree sampling and prime-factor-count shift invariance is credited (README:61-67; paper 1.1).

## Blocker summary

C1 through C5 must be fixed before freezing. C1, C2, C3 and C5 are README-only edits. C4 also touches paper 1.1, which changes main.tex and main.pdf, so the MANIFEST and PDF must be regenerated.
