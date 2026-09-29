# Audit ledger

Append-only. The release owner integrates every edit; auditors were read-only
except for their single assigned report. Auditors are process-separated AI
agents (same provider), not independent experts; nothing here is peer review.

## Pins

| Item | Value |
|---|---|
| Drafting source | `consolidated-proof.tex`, SHA-256 `4f01b8a7b08749251fe1784ef1fc34c82283a6b6622cb7d9077a1a6d83bbf15b` |
| Drafting reading copy (13 pp.) | SHA-256 `3ef993bb66020701d2afbcfee429a713abc99c25a3b0568e157431b21e9d22a9` |
| Audit packet | commit `d199bfb`; `paper/main.tex` `3533d5f0ec0aa061a8208dbb8be589fec1b4845c23c0aeebe822545b35f0b519`; `paper/main.pdf` (14 pp.) `9121f4247da3a2fee67b99cfb4f43c28a45841de1d08583c300d93c47c4987e3`; `README.md` `aaa916bdcbb42cb415e3e21ce2a675dffea9738d72e575bc424e8659223e24c8` |

Release edits to the drafting source at `d199bfb`: author and version line;
removal of a draft-status paragraph; one abstract sentence stating that the
depth bound gives no rate for M(n)/n; one scope sentence relating T to the
author's earlier sparse-matrix release, with its citation added. No theorem,
lemma, or proof text changed.

## Audits (2026-09-28)

| Report | Lane | Exposure | Model tier | Verdict |
|---|---|---|---|---|
| `reports/owner-proof-review.md` | proof, owner | manuscript first, then drafting reviews | root agent | no defect; INTERNAL-NONINDEPENDENT |
| `reports/initial-failure-search.md` | isolated failure search | statement packet only | frontier | NOT-BROKEN |
| `reports/proof-audit.md` | full proof audit | frozen manuscript only | frontier | VERIFIED; no must-fix |
| `reports/prior-art-audit.md` | citations and bounded prior art | frozen manuscript, primary sources | frontier | citations PARTIAL; attribution PASS; novelty PARTIAL |
| `reports/claim-prose-audit.md` | claim and public prose | frozen README, manuscript, PDF | mid tier | PARTIAL |

## Findings and dispositions

| ID | Source | Finding | Disposition |
|---|---|---|---|
| C1 | claim-prose | README uses μ before defining it | Fixed: README defines μ in the introduction |
| C2 | claim-prose | README uses d, reciprocal weights, and moving windows without explanation | Fixed: README explains the multiplier bias, the window n^c < p ≤ n^β, and weights ∝ 1/p |
| C3 | claim-prose | "stops changing in distribution" overstates a limsup bound | Fixed: reworded to "consecutive depths give nearly the same distribution once K is large" |
| C4 | claim-prose | Parity testing not explicitly disclaimed as new | Fixed in README ("Standard tools" bullet) and in the last paragraph of paper Section 1.1 |
| C5 | claim-prose | "process-separated AI audits" called jargon | Declined: this is the release standard's prescribed description, chosen so that separate contexts are not presented as independent experts |
| C6–C10 | claim-prose | optional style and date notes | C7/C8: TV now defined in words in the README; others noted, no change |
| F1 (report E1) | failure search | Corollary deduction and factor two sound | No action |
| F5 (report E6) | failure search | Claims statement 4 (Lemma 6.2) alone implies ζ(1+iγ) ≠ 0, so the PNT's difficulty must hide in its large-frequency step | Rejected after owner check. The inference assumes a zero would force |E p^{iγ₀}| → 1 in the window; the envelope f_n ≤ J/(Hx) (from the Chebyshev-type Lemma 2.3) forbids such concentration, and Lemma 6.2 Step 1 proves |φ_n(t)| ≤ κ from the envelope alone, for every |t| > T₀ including frequencies growing with n. As in Richter's proof, the integer structure enters through squarefree counting (Lemma 2.1) in Proposition 3.1, not through the prime smoothing. Step 1 is also in the fresh proof audit's scope, which verified it. The report labels E6 UNRESOLVED as a proof risk; the owner disposition above supersedes that label only for this release's purposes and the report is unchanged |
| F7 (report E8) | failure search | Statement 1 is vacuous when B_{d+1} is empty (small K) | No change: Theorem 1.1 is for sufficiently large K, and Section 3 assumes Z_h > 0 |
| P1 | proof audit F1 | a = min(1/4, η/[2(d+1)]) always equals the second term | Fixed: a = η/[2(d+1)] ≤ 1/4; "for large d" removed in Section 7 |
| P2 | proof audit F2 | letter c reused for absolute constants | Fixed: Q(x) ≥ x/2 (so P(p divides a) ≤ 2/p); c → c₀ in Section 7 |
| P3 | proof audit F3 | R reused as frequency cutoff | Fixed: renamed T₁ |
| P4 | proof audit F4 | elementary symmetric bound used silently in Lemma 4.1 | Fixed: stated |
| P5 | proof audit F5 | P(S\|b) reads as conditional probability | Fixed: renamed π_S |
| P6 | proof audit F6 | Cη term holds with C = 1 | Fixed: written as η in Proposition 3.1 and Section 7 |
| P7 | proof audit F7 | C_F unstated | Fixed: C_F = 4π², inner integral 2π (owner re-derived) |
| P8 | proof audit F8 | test functions need restriction to the common support | Fixed: stated |
| P9–P10 | proof audit F9–F10 | optional wording | No change |
| P11 | proof audit F11 | prior art outside that lane | Covered by the prior-art lane |
| A-F1 | prior art F1 | Koukoulopoulos has a journal version | Fixed: Compositio Math. 149 (2013), no. 7, 1129–1149, doi:10.1112/S0010437X12000802 (owner confirmed on Crossref) |
| A-F2 | prior art F2 | assuming PNT, the statement of Theorem 1.1 may follow from standard anatomy asymptotics, possibly with a better rate | Accepted as a qualification, not as a verified derivation. Paper Section 1.1 and README now say the statement alone is not claimed as new, the contribution is the PNT-free proof and the uniform matching estimate, and the rate is not claimed sharp. Lead on the deletion theorem kept. The PNT-based comparison is an open residual |
| A-F3 | prior art F3 | moving-window Richter variant might give the qualitative limit | Fixed: stated in Section 1.1 and README as unchecked |
| A-F4 | prior art F4 | Bergelson–Richter's proof of Lemma 2.2 uses the PNT | Fixed: stated. Owner confirmed in the arXiv v3 text: the proof of Lemma 2.2 opens "It is a consequence of the Prime Number Theorem that ..." |
| A-F5 | prior art F5 | LWWY Theorem 1.2 mischaracterized | Fixed: now "Theorem 1.2(1) proves an equidistribution statement ... largest prime factor in a prescribed set of primes of natural density" |
| A-F6 | prior art F6 | published Richter proof of Prop. 2.2 corrected only in arXiv v3 | Fixed: bibliography note |
| A-F7 | prior art F7 | credit Daboussi and Kátai for the averaging criterion | Fixed in text ("which Richter and Bergelson–Richter trace to Daboussi and Kátai"); no bibliography entries added because their details could not be verified from the originals |
| A-F8 | prior art F8 | add DOIs | Fixed for Richter, Bergelson–Richter, LWWY, Koukoulopoulos (Crossref confirmed); LWWY issue number dropped, since Crossref lists none |
| A-F9–F11 | prior art F9–F11 | optional (Arratia publisher, Prohorov, Chen arXiv:2608.05191) | No change; Chen recorded as an unresolved comparison |

## Report hashes and redaction

Reports as delivered by the auditors (SHA-256):

| Report | As delivered |
|---|---|
| `reports/claim-prose-audit.md` | `166f5a3c32429b4fab02f2ad15f64352e53e4b0c4935e34be24686465d49febc` |
| `reports/initial-failure-search.md` | `21eeadf4a9a011687a4cda76d821f21ee7ace3675582b048d3c03ff051eb14f8` |
| `reports/prior-art-audit.md` | `18973daf01f381b5cd5a23a4a3c2b725d65b1507d19d68d565848e23a2018620` |
| `reports/proof-audit.md` | `74380345c923db019b6093b892a9ab0e797d5e1e27ac6fcd74bc85adae622e67` |

On 2026-09-28 the owner redacted a local interpreter path and a scratch-directory
reference in the "Tools" line of `reports/initial-failure-search.md`. The
redaction is marked in the text. No finding or verdict was changed. The probe
scripts are not part of the release.

## Integration check (2026-09-28)

`reports/integration-check.md` (mid-tier agent, fresh context, read-only) checked commit `89fc184` against `d199bfb`. All mathematical edits are correct, and all "Fixed" rows are present. Overall PARTIAL on record gaps only:

| ID | Finding | Disposition |
|---|---|---|
| I1 | `MANIFEST.sha256` not yet tracked | Fixed: manifest generated and committed at freeze |
| I2 | VERIFICATION points to a PDF hash absent from ADMISSION | Fixed: hash added to ADMISSION; clean-archive rebuild rerun on the frozen commit |
| I3 | tracked-tree scan not recorded | Fixed: scan recorded below |
| I4 | CFF abstract omits "rate not claimed sharp" | Fixed |
| I5 | Section 1.1 lacks the no-rate clause | Declined: stated in the abstract, Section 1, and Section 9; not worth changing the frozen PDF |
| I6 | ADMISSION principal claim omits the matching estimate | Fixed |
| I7 | failure-search labels E1/E6/E8 vs ledger F1/F5/F7 | Fixed: mapping added |
| I8 | CFF message "Please cite Version 0.1.0" | Declined: the message must be timeless because Zenodo imports it; status lives in README and ADMISSION |

## Hygiene scan (2026-09-28)

A `git grep` for local home and temporary-directory paths, the local account
name, scratch and agent-tool directories, placeholder markers (TODO, XXX, TBD),
and personal email addresses, run over all tracked files except LICENSE, and over every commit in the history
(`git rev-list --all`). Result after the redaction above: no matches. The scan
is rerun on the frozen commit.
