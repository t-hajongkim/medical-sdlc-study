# Plan: CLEAR — an auditable foundation model for radiology grounded in clinical concepts

- Issue: https://github.com/t-hajongkim/medical-sdlc-study/issues/2
- Paper: `recommended/2026-08-20/clear-auditable-radiology-foundation-model/paper.json`
- DOI: https://doi.org/10.1038/s41551-026-01741-4
- Physician focus: Whether CLEAR's concept-based auditing helps a cohort with
  very few Nodule cases, specifically the risk of missed nodules (false
  negatives), and how our Nodule subgroup's size, view-position mix (PA/AP),
  and demographics compare to CLEAR's external validation cohorts.

## Proposed presentation

- **Chart 1 — bar chart, findings-label distribution (all labels vs. Nodule
  slice highlighted).** X-axis: label, Y-axis: count. Encodes how rare Nodule
  (7/272, ~2.6%) is relative to "No Finding" (145) and other pathologies. This
  directly supports the physician's opening question ("does this work when
  Nodule cases are scarce?") by making the class-imbalance magnitude visible
  before any performance claim is made.
- **Chart 2 — pie or stacked-bar, view position within the Nodule subgroup
  (PA vs. AP) next to the same split for the whole cohort.** Encodes the
  physician's second question directly: our Nodule cases are 10 PA / 2 AP
  (83%/17%), close to but not identical to the cohort-wide 184/88 (68%/32%)
  split. A side-by-side comparison chart (not just numbers in prose) makes
  the "how different" comparison immediate, since AP views have different
  geometry/exposure and could affect false-negative risk differently than PA.
- **Table — Nodule subgroup vs. paper's validation cohorts** (size, age,
  sex, view mix, institution/device spread) placed before the charts, since
  the physician's core ask is a numeric comparison, not a narrative.
- **Text sections, in order:** (1) one-paragraph summary of CLEAR's claim
  relevant to false negatives (concept-level auditing, zero-shot pathology
  detection), (2) the Nodule-subgroup numbers (n=7 pure Nodule + 4 multi-label
  combinations = 12 total studies containing Nodule, from 12 unique
  age/sex rows, ages 32–77), (3) explicit statement of what remains unknown
  (no local sensitivity/false-negative rate can be computed without ground
  truth adjudication and a run of the model, which is out of scope here).
- **Layout order:** table first (grounds the numeric comparison the
  physician asked for), then the two charts (label rarity, then view-position
  mix), then text/caveats last, ending with the open questions.

## Open questions

- Should "Nodule" subgroup include only the pure `Nodule` label (n=7) or all
  studies where Nodule co-occurs with other findings (n=12 total)? This
  changes every downstream count.
- Does the physician want a proxy false-negative analysis using zero-shot
  CLEAR inference on our images, or only a data-characteristics comparison
  (no model run) for this first pass?
- Is the 2:10 AP:PA imbalance within Nodule cases (vs. 88:184 cohort-wide)
  worth stratifying on, or is n=12 too small to say anything about AP-specific
  risk?
- Should device/institution spread (11 distinct institution/device pairs for
  12 Nodule studies) be treated as a confound to control for, or reported only
  descriptively given the small counts?
