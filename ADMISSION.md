# Admission record

**Current state:** ADMITTED

**Version:** 0.1.0

**Tag:** `v0.1.0` → `413f02271f834043af6e61fefc8b7b9e04e1a100` (annotated tag object `969eb23`)

**Standard:** [A Public Standard for This Work](https://jeff-kline.github.io/posts/research-program/index.html), draft 0.4, 2026-08-01

Current verdict: ADMITTED (2026-09-29)

**Version DOI:** [`10.5281/zenodo.23038366`](https://doi.org/10.5281/zenodo.23038366) · **Concept DOI:** `10.5281/zenodo.23038365` · **Record:** <https://zenodo.org/records/23038366>

Admission is a project release decision. It is not peer review, a correctness
certificate, or proof of global novelty.

## Principal claim

Let `U_n` be uniform on the squarefree integers in [1, n], let T delete the
largest prime factor (with T(1) = 1), and let `ν_{n,K}` be the law of
`T^K(U_n)`. Then, for all sufficiently large K,

`limsup_{n→∞} TV(ν_{n,K}, ν_{n,K+1}) ≤ C (log K)^(−1/4)`

with an absolute constant C. The limit in n is taken with K fixed. Testing
against the Möbius function gives `M(n) = o(n)`, the classical Möbius form of
the prime number theorem; that equivalence is taken as known. The technical
contribution is a uniform matching estimate for products of d and d + 1 primes
from a moving window (Proposition 6.3). The proof does not assume the prime
number theorem and uses Plancherel's theorem. It gives no rate for `M(n)/n`
and no new error term. The statement of the deletion theorem alone is not
claimed as new, and the rate is not claimed to be sharp.

## P1 — prior work and credit

| Check | Status | Evidence or residual |
|---|---|---|
| Closest mechanisms and parameter families compared | PASS | Richter, Bergelson–Richter, Li–Wang–Wang–Yi, Arratia, and Nourdin–Poly compared at named statements (`audit/reports/prior-art-audit.md`); direct substitution of fixed multipliers ruled out by Remark 2.5 |
| Obtainable primary sources checked | PASS | arXiv versions of all cited works; Crossref records for DOIs; the owner confirmed Bergelson–Richter's use of the PNT in the proof of Lemma 2.2 |
| Contribution types distinguished | PASS | Paper Section 1.1 and README: the PNT-free proof and the uniform matching estimate are put forward; the statement alone, the averaging principle, squarefree sampling, parity testing, and the Fourier identity are not |
| Novelty bounded to searched corpus | PASS | Section 1.1's final paragraph and README "Contribution and prior work" |
| Inaccessible or unresolved comparisons visible | PASS (named residuals) | Unread originals: Daboussi (1975, 1984) and Kátai (1986), credited through Richter and Bergelson–Richter; published BLMS, Duke, Acta Arith., and Compositio PDFs, with arXiv versions used; Knuth–Trabb Pardo; Chen arXiv:2608.05191, abstract only. Not carried out: a PNT-based derivation of the statement, and a moving-window variant of Richter's construction. All are named in the paper or in `audit/` |

**P1 gate:** PASS with named residuals. Priority is qualified to the searched
corpus.

## A1 — claim and artifact consistency

| Check | Status | Evidence or residual |
|---|---|---|
| Principal claim precise and no broader than proof | PASS | `audit/reports/proof-audit.md` (VERIFIED), `audit/reports/owner-proof-review.md` |
| Parameters, quantifier order, and limitations near the claim | PASS | Abstract, Theorem 1.1, Section 1, Section 9, and README Introduction |
| Proof, computation, and literature separated | PASS | No theorem rests on computation; README "Evidence and limits" |
| Prior work credited near the claims | PASS | Section 1.1; `audit/LEDGER.md` A-F1 to A-F8 |
| Public prose plain and free of process history | PASS | `audit/reports/claim-prose-audit.md` and `audit/reports/refreeze-claim-check.md`, dispositions in the ledger |
| Title, author, version, and status agree | PASS | README, living PDF title page and metadata, `CITATION.cff`, this file, and the Zenodo record |
| Adversarial checking | PASS | Isolated failure search NOT-BROKEN; fresh full proof audit VERIFIED; integration and refreeze checks of later edits; all findings dispositioned in `audit/LEDGER.md`. These are AI audits, not peer review |

**A1 gate:** PASS. Theorem statements and proofs are unchanged since the proof
audit; the 2026-09-29 title and prose revision was checked separately.

## R1 — release and stewardship

| Check | Status | Evidence or residual |
|---|---|---|
| Reproduction commands and pinned tools | PASS | `VERIFICATION.md` |
| Deterministic build from a clean archive | PASS | `git archive b78722d` extraction rebuilds the tagged `paper/main.pdf` byte-identically (SHA-256 `bb59bd84ba633980aad5c1df93d233ebca0cd5529a6309fb6912e0c3c1495e1f`) |
| Complete tracked-file manifest | PASS | `MANIFEST.sha256`; the tagged archive's internal manifest also verifies |
| Hygiene: credentials, private paths, placeholders | PASS | Tracked-tree and history scan, recorded in `audit/LEDGER.md` |
| Correction, withdrawal, and supersession policy | PASS | `CORRECTIONS.md` |
| Machine-readable citation | PASS | Living `CITATION.cff` carries the version DOI and release date; the tagged copy is candidate-safe |
| Immutable semantic tag | PASS | Annotated `v0.1.0` (object `969eb23`) → `413f022`; tagger is the GitHub noreply identity |
| Public permanent archive with provider byte identity | PASS | Two pinned GitHub `zipball/v0.1.0` downloads and two Zenodo downloads are byte-identical: 412,038 bytes, SHA-256 `c133d8ba364f29266aa4f6440c3286fe50d536993c79e548a112bb55de96d7ae`; Zenodo MD5 `d415cc11d7352eee33e08184cc1e77d7` |
| DOI resolves; living repository identifies the version | PASS | `doi.org/10.5281/zenodo.23038366` redirects to the Zenodo record; README, `CITATION.cff`, and the living paper carry the version DOI |
| Archive metadata matches repository | PASS | Title, creator Kline, Jeffery, version v0.1.0, publication date 2026-09-29, license `gpl-3.0-only` (GNU GPL v3.0 only), resource type software, related identifier the `v0.1.0` tree |

**R1 gate:** PASS.

## Named residual risks

- No human expert has reviewed the proof; the audits are same-provider AI
  audits in separate contexts.
- The prior-art comparison is bounded. A PNT-based derivation of the deletion
  statement, a moving-window variant of Richter's construction, and several
  unread originals remain open comparisons.

## External actions

| Action | Owner | Status |
|---|---|---|
| Local edits, builds, audits | release agent | done |
| Create GitHub repository `jeff-kline/largest-prime-deletion` | release agent, authorized by author | done 2026-09-29 |
| Push `main`; make repository public | release agent, authorized by author | done 2026-09-29 |
| Enable the repository in Zenodo (web portal) | author | done 2026-09-29 |
| Annotated tag `v0.1.0` and GitHub Release | release agent, authorized by author | done 2026-09-29T10:50Z |
| Zenodo record verification | release agent | done 2026-09-29 |
| Living metadata commit | release agent, authorized by author | done with this commit |
| Public-site listing on jeff-kline.github.io | release agent, authorized by author | done 2026-09-29: site commit `0917fa1`, deployed; live HTML shows the title, the author's blurb, the repository link, and the version DOI |
