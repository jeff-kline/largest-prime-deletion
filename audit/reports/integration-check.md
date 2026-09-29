# Integration check of 89fc184 against d199bfb

Read-only. Method: `git diff d199bfb 89fc184 -- paper/main.tex README.md`, reading the release records, `pdfinfo`, `pdftotext`, `shasum` on git blobs. No build was run, so PDF byte-identity from a clean build is not re-verified here.

## Overall: PARTIAL

All mathematical edits are correct and harmless, and all ledger "Fixed" rows are present in the files. The claim-consistency points hold with two minor gaps. Three release-record statements are contradicted by the repository (missing MANIFEST.sha256, a PDF hash that ADMISSION.md is said to record but does not, a hygiene scan the ledger is said to contain but does not). These are record defects, not proof defects.

## Task 1: mathematical edits in main.tex (all verified, none introduces an inconsistency)

- a = η/[2(d+1)] ≤ 1/4: true for 0 < η ≤ 1, d ≥ 1 (a ≤ 1/(2·2)). Consistent with Prop. 6.3 (J ≤ C(1+log((d+1)/η))) and with the display (2d+1)a < η. Section 7 "Here a = 1/[2d(d+1)]" matches η = 1/d. Removing "for large d" is right.
- Q(x) ≥ x/2: Q(x) = (6/π²)x + O(√x) with 6/π² ≈ 0.608, so it holds for large x. P_{U_x}(p | a) ≤ ⌊x/p⌋/Q(x) ≤ 2/p is correct. The union bound still gives O_h(Y^{-1}) with C = 2h.
- C_F = 4π²: with ĝ(t) = ∫e^{itx}g and [v]² = ∬|v(s)−v(t)|²/|s−t|², Plancherel gives 2π∫|e^{irx}−1|²|g|², and ∫|e^{iu}−1|²/u² du = 4∫sin²(u/2)/u² du = 2π. So C_F = 2π·2π = 4π². The later use "2C_F h²κ^{2h−2}(J+1)/H" is unaffected.
- Cη → η: 1 − e^{−η} ≤ η holds, and the displayed line already ended in "≤ η + o(1)". Prop. 3.1 and Section 7 both say η. No stale "Cη" remains.
- R → T_1: only the frequency cutoff was renamed, in the Step 3 paragraph (five occurrences). The remaining R is the multiplier bound R = n^ε in Sections 3 and following, which is a different object and is not affected. No stale frequency-R remains.
- P(S|b) → π_S: one definition, no other uses of the old notation. (π_S is not used elsewhere in the paper, and the symbol π(z) elsewhere is a different object. This is harmless.)
- Elementary symmetric sum: e_r(x_1,...,x_N) ≤ (Σx_i)^r/r! for nonnegative x_i is true (every r-subset product appears r! times in the expansion of the r-th power). Combined with Σ(p−1)/p² ≤ Σ1/p = H_0, the displayed bound follows.
- c → c_0 in Section 7 is consistent with line 78 ("C or c_0 absolute") and with Prop. 6.3.
- Text edits in 1.1 (LWWY Thm 1.2(1), PNT use in BR Lemma 2.2, Daboussi–Kátai, moving-window caveat), bibliography DOIs and Richter footnote note: no mathematical content, consistent with ledger.

## Task 2: LEDGER "Fixed" rows

All present at 89fc184: C1, C2, C3, C4 (README "Standard tools" bullet and the last paragraph of Section 1.1), C7/C8 (TV in words), P1, P2, P3, P4, P5, P6, P7, P8 ("bounded and continuous on the common support"), A-F1, A-F3, A-F4, A-F5, A-F6, A-F7, A-F8. A-F2 (accepted qualification) present in both places. None missing. Ledger pins verified: d199bfb main.tex, main.pdf, README hashes match; the three unredacted report hashes match; the failure-search report differs, as disclosed by the redaction note.

## Task 3: consistency of the four points

| Point | Paper 1.1 | README | CITATION abstract | ADMISSION principal claim |
|---|---|---|---|---|
| Put forward: PNT-free proof + uniform matching estimate | yes | yes | yes (PNT not assumed; uniform Fourier matching estimate) | PNT-free yes; uniform matching estimate only in the P1 table, not the principal claim |
| Statement alone not claimed new | yes | yes | yes | yes |
| Rate not claimed sharp | yes | yes | absent | yes |
| No M(n)/n rate | not in 1.1 (in abstract, line 78, Sec. 9) | yes (Limits paragraph) | yes | yes |

"Strictly elementary" is never claimed. README line 55 and paper line 568 explicitly disclaim it, and the other files say only "elementary prime estimates and Plancherel's theorem".

## Task 4: title, author, version, status

Title "Total variation under largest-prime deletion", author Jeffery Kline, and version 0.1.0 agree in README, CITATION.cff, PDF title page and pdfinfo (Title, Author, Subject "Version 0.1.0, release candidate"). ADMISSION says CANDIDATE, 0.1.0 (it has no title line, which is fine). CITATION.cff has no doi and no date-released. main.pdf at 89fc184 (sha256 2dd08930...) contains the new Section 1.1 text (checked by pdftotext: "not available to an argument", Daboussi and Kátai, LWWY prescribed set of primes, thinned prime pools, not claimed to be sharp, standard device, proved without assuming, Richter footnote), T_1, and π_S. It has 14 pages and a creation date of 2026-09-28 00:00 UTC (SOURCE_DATE_EPOCH). The working tree is clean.

## Task 5: CORRECTIONS / VERIFICATION / ADMISSION versus the repository

See findings 1 to 3 below. No other contradictions were found. The integrated-diff-check claim is pending, as instructed, and this report is that check.

## Findings

| id | must-fix / optional | file:line | finding | minimal fix |
|---|---|---|---|---|
| I1 | must-fix | ADMISSION.md:61; VERIFICATION.md:9,38; README.md (Reproduce, Repository contents) | `MANIFEST.sha256` is not tracked at 89fc184 (`git ls-files` shows none), yet ADMISSION marks "Complete tracked-file manifest" PASS and VERIFICATION says every tracked file matches it. | Generate and commit the manifest (listing all tracked files except itself), or mark the row pending until it exists. |
| I2 | must-fix | VERIFICATION.md:60 | Says the SHA-256 of the rebuilt PDF "is recorded in ADMISSION.md". ADMISSION.md contains no hash. The PDF at 89fc184 is 2dd08930f32d66cf575c0db9a19baf89f179318164b997819c95692198d1c562, which differs from the audit-packet PDF (9121f424...). | Add the hash to ADMISSION.md, or change the sentence to point to the manifest. Re-run the clean-checkout rebuild on the final commit, since this check did not build. |
| I3 | must-fix | ADMISSION.md:62 | "Tracked-tree scan (see ledger)": audit/LEDGER.md has no scan record. | Add a ledger entry stating the scan and its result, or drop "(see ledger)". |
| I4 | optional | CITATION.cff:12-25 | Abstract omits "rate not claimed sharp", which the other three documents state. | Append "The rate is not claimed to be sharp." |
| I5 | optional | paper/main.tex:92 (Section 1.1) | The no-rate-for-M(n)/n statement is not repeated in Section 1.1 (it is in the abstract, line 78, and Section 9). | Optionally add one clause; not required for consistency. |
| I6 | optional | ADMISSION.md:20-27 | Principal claim does not mention the uniform matching estimate, which paper and README name as the second contribution. | Add "and the uniform matching estimate (Proposition 6.3)". |
| I7 | optional | audit/LEDGER.md:44-46 vs reports/initial-failure-search.md:15-172 | Ledger cites failure-search items F1, F5, F7. The report's headings are E1, E6, E8, and E6 is labelled "UNRESOLVED as a proof-risk only" while the ledger says "Rejected". | Add a mapping (F1=E1, F5=E6, F7=E8) and say the report label predates the owner's disposition. |
| I8 | optional | CITATION.cff:2 | "Please cite Version 0.1.0" while README says no stable citation exists and CITATION has no "release candidate" marker. | Reword the message: "Release candidate 0.1.0; no DOI yet." |
