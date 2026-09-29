# Admission record

**Current state:** DRAFT (prose revision of the private 0.1.0 candidate; pending refreeze; not tagged or archived)

**Version:** 0.1.0

**Standard:** [A Public Standard for This Work](https://jeff-kline.github.io/posts/research-program/index.html), draft 0.4, 2026-08-01

**Verdict:** not yet admitted. Admission would require the tag, the permanent
archive, and the byte-identity checks below. Admission is a project release
decision. It is not peer review, a correctness certificate, or proof of
global novelty.

## Principal claim

Let `U_n` be uniform on the squarefree integers in [1, n], let T delete the
largest prime factor (with T(1) = 1), and let `ν_{n,K}` be the law of
`T^K(U_n)`. Then, for all sufficiently large K,

`limsup_{n→∞} TV(ν_{n,K}, ν_{n,K+1}) ≤ C (log K)^(−1/4)`

with an absolute constant C. The limit in n is taken with K fixed. Testing
against the Möbius function gives `M(n) = o(n)`, the classical Möbius form of the prime number theorem. The technical contribution is a uniform matching estimate for products of d and d + 1 primes from a moving window (Proposition 6.3). The proof does not assume
the prime number theorem and uses Plancherel's theorem. It gives no rate for
`M(n)/n` and no new error term. The statement of the deletion theorem alone
is not claimed as new, and the rate is not claimed to be sharp.

## P1 — prior work and credit

| Check | Status | Evidence or residual |
|---|---|---|
| Closest mechanisms and parameter families compared | PASS | Richter, Bergelson–Richter, Li–Wang–Wang–Yi, Arratia, and Nourdin–Poly compared at named statements (`audit/reports/prior-art-audit.md`); direct substitution of fixed multipliers ruled out by Remark 2.5 |
| Obtainable primary sources checked | PASS | arXiv versions of all cited works; Crossref records for DOIs; the owner confirmed Bergelson–Richter's use of the PNT in the proof of Lemma 2.2 |
| Contribution types distinguished | PASS | Paper Section 1.1 and README: the PNT-free proof and the uniform matching estimate are put forward; the statement alone, the averaging principle, squarefree sampling, parity testing, and the Fourier identity are not |
| Novelty bounded to searched corpus | PASS | Section 1.1's final paragraph and README "Contribution and prior work" |
| Inaccessible or unresolved comparisons visible | PARTIAL | Unread originals: Daboussi (1975, 1984) and Kátai (1986), credited through Richter and Bergelson–Richter; published BLMS, Duke, Acta Arith., and Compositio PDFs, with arXiv versions used; Knuth–Trabb Pardo; Chen arXiv:2608.05191, abstract only. Not carried out: a PNT-based derivation of the statement, and a moving-window variant of Richter's construction. All are named in the paper or in `audit/` |

**P1 gate:** PASS with named residuals. Priority is qualified to the searched
corpus.

## A1 — claim and artifact consistency

| Check | Status | Evidence or residual |
|---|---|---|
| Principal claim precise and no broader than proof | PASS | `audit/reports/proof-audit.md` (VERIFIED), `audit/reports/owner-proof-review.md` |
| Parameters, quantifier order, and limitations near the claim | PASS | Abstract, Theorem 1.1, Section 1, Section 9, and README Introduction |
| Proof, computation, and literature separated | PASS | No theorem rests on computation; README "Evidence and limits" |
| Prior work credited near the claims | PASS | Section 1.1; `audit/LEDGER.md` A-F1 to A-F8 |
| Public prose plain and free of process history | PASS | `audit/reports/claim-prose-audit.md` findings C1–C4 fixed; draft-status paragraph removed |
| Title, author, version, and status agree | PASS | README, PDF title page and metadata, `CITATION.cff`, this file |
| Adversarial checking | PASS | Isolated failure search NOT-BROKEN; fresh full proof audit VERIFIED; all findings dispositioned in `audit/LEDGER.md`. These are AI audits, not peer review. The integrated diff received its own read-only check (`audit/reports/integration-check.md`, PARTIAL on record gaps only; dispositions in the ledger) |

**A1 gate:** reopened for the 2026-09-29 prose revision. Abstract, introduction, README, and citation abstract were aligned in a local editorial review; theorem statements, equations, and proof bodies are unchanged. Earlier audit PASS rows above describe the prior candidate. Refreeze the revised tree before release.

## R1 — release and stewardship

| Check | Status | Evidence or residual |
|---|---|---|
| Reproduction commands and pinned tools | PASS | `VERIFICATION.md` |
| Deterministic build from a clean archive | PENDING REFREEZE | Prior candidate passed. The revised source built twice from empty auxiliary state with identical bytes (14 pages; SHA-256 `bb59bd84ba633980aad5c1df93d233ebca0cd5529a6309fb6912e0c3c1495e1f`); a clean committed-archive check remains to be rerun. |
| Complete tracked-file manifest | PASS | `MANIFEST.sha256` |
| Hygiene: credentials, private paths, placeholders | PASS | Tracked-tree and history scan, recorded in `audit/LEDGER.md` |
| Correction, withdrawal, and supersession policy | PASS | `CORRECTIONS.md` |
| Machine-readable citation | PASS | `CITATION.cff`, candidate-safe: no DOI, no release date |
| Immutable semantic tag | FAIL (not yet authorized) | Proposed: annotated `v0.1.0` at the frozen candidate commit |
| Public permanent archive with provider byte identity | FAIL (not yet authorized) | Proposed route: Zenodo GitHub integration |
| DOI resolves; living repository identifies the version | FAIL (not yet authorized) | — |
| Archive metadata matches repository | FAIL (not yet authorized) | — |

**R1 gate:** open. It can close only after the authorized tag, GitHub Release,
and Zenodo archive, and verification of the downloaded record.

## External actions

| Action | Owner | Status |
|---|---|---|
| Local edits, builds, audits | release agent | prior candidate done; 2026-09-29 editorial revision awaits refreeze |
| Create GitHub repository `jeff-kline/largest-prime-deletion` | prior release agent | private repository created, per author report |
| Push `main` | prior release agent | prior candidate pushed, per author report; editorial revision not pushed |
| Enable the repository in Zenodo (web portal) | author | not done |
| Annotated tag `v0.1.0` and GitHub Release | author approval required | not done |
| Zenodo record verification | release agent, after the release | not done |
| Public-site listing on jeff-kline.github.io | author approval required | not proposed yet |
