# Corrections, withdrawals, and supersession

This repository keeps a visible record of material corrections to released
claims and artifacts.

## Policy

- Minor typographical or navigational fixes may be made on the living default
  branch without changing an archived release.
- A change to a theorem statement, hypothesis, proof dependency, citation that
  affects priority or scope, or verification artifact creates a new version.
  The earlier tag and permanent archive remain unchanged and identifiable.
- A material error that invalidates a principal claim will be marked
  prominently in the README and in this file. The affected release will not be
  deleted or silently replaced.
- A withdrawn result remains findable with the reason, date, affected
  versions, and any replacement or correction linked here.
- Public tags and archived files are immutable. Corrections are made in a new
  commit and, when material, a new tagged release.
- If earlier work is found that anticipates a result here, the novelty
  statements will be narrowed and the source credited in a new version.

Suspected errors may be reported through the repository issue tracker:
<https://github.com/jeff-kline/largest-prime-deletion/issues>.

## Version history

### 0.1.0 — released 2026-09-29

- Tag `v0.1.0` at commit `413f022`; version DOI
  [`10.5281/zenodo.23038366`](https://doi.org/10.5281/zenodo.23038366), concept DOI `10.5281/zenodo.23038365`.
- The tagged snapshot retains its prepublication "release candidate" wording
  and carries no DOI, because Zenodo minted the DOI after the GitHub Release.
  The living repository and paper now carry the active DOI; the archived files
  were not changed. The living PDF differs from the tagged one only in its
  title-page version line and PDF metadata.

#### Release preparation, before the tag

- Between the first frozen candidate (`2da63c1`, 2026-09-28) and the tag, the
  author directed a prose revision that leads with the prime number theorem in
  its Möbius form, and retitled the paper from "Total variation under
  largest-prime deletion" to "The prime number theorem via largest-prime
  deletion". Theorem statements and proofs did not change.

- Release preparation began 2026-09-28 from a drafting manuscript with SHA-256
  `4f01b8a7b08749251fe1784ef1fc34c82283a6b6622cb7d9077a1a6d83bbf15b` (13-page
  reading copy `3ef993bb66020701d2afbcfee429a713abc99c25a3b0568e157431b21e9d22a9`).
- Prepublication changes before any tag are listed in `audit/LEDGER.md`.
