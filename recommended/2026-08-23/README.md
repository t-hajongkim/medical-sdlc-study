# Daily Paper Recommendations — 2026-08-23

**Research date:** 2026-08-23 (yesterday in Asia/Seoul)
**Actual search window used:** 2026-07-25 to 2026-08-23 (30-day window; the 1-day
window returned nothing and the 7-day window returned only one paper already
insufficient to reach the 3-paper target)
**Search query:** `chest X-ray deep learning diagnosis`

## Cohort snapshot (aggregate only, no patient-level values)

- 272 chest X-ray studies from 153 masked patients.
- Sex nearly balanced (136 M / 136 F), mean age ≈ 51.5.
- View position: 184 PA, 88 AP.
- Findings label distribution (top labels): "No Finding" (145), Infiltration (21),
  Atelectasis (16), Nodule (7), Fibrosis (6), Effusion (6), Cardiomegaly (5),
  Effusion+Infiltration (5), Pneumothorax (5), Emphysema (4), plus several
  low-count multi-label combinations (Atelectasis/Effusion/Infiltration/
  Consolidation/Emphysema/Pleural_Thickening/Pneumothorax).
- This is a modest, multi-pathology plain chest radiograph cohort with a long
  tail of rare/low-prevalence findings, and report text/clinical info fields
  available per study — good ground for evaluating generalization and
  long-tail diagnostic performance.

## Retained papers

### 1. Advancing human-centric AI for robust X-ray analysis through holistic self-supervised learning (RayDINO)
*Nature Communications, 2026* — https://doi.org/10.1038/s41467-026-76076-4

**Why relevant:** RayDINO is a self-supervised chest X-ray encoder trained on
840,000 images and evaluated on 82,000 images from 12 public datasets across
nine radiology tasks, with an explicit analysis of population, age, and sex
biases.

**What our data supports:** our cohort's balanced age/sex distribution and
mixed PA/AP views are exactly the kind of population-level slice RayDINO's
bias analysis is designed to probe; the paper's task-specific adapters could
be applied to our multi-label findings without large local retraining.

**What it cannot tell us:** RayDINO was not evaluated on our specific
institution/device mix, so local calibration and bias re-assessment on our
153-patient cohort would still be required before use.

### 2. Multicenter evaluation of four large language models for automated spine imaging diagnosis
*npj Digital Medicine, 2026* — https://doi.org/10.1038/s41746-026-03133-z

**Why relevant:** this multicentre study of 20,277 real spine reports across
three hospitals directly quantifies a "long-tail diagnostic deficit" — high
overall performance (specificity >90%, NPV >96%) but 19–42 percentage-point
precision loss for low-prevalence conditions, plus prompt-sensitivity effects.

**What our data supports:** our findings distribution has the same long-tail
shape (a few common labels like Infiltration/Atelectasis vs. many single- or
low-digit-count combinations such as Fibrosis, Pleural_Thickening, and
multi-label rarities), making the paper's prevalence-dependent precision
warning directly applicable to any LLM-based report analysis on our data.

**What it cannot tell us:** it studies spine reports, not chest X-ray images
or reports, so quantitative error rates cannot be transferred directly; only
the qualitative long-tail/prompt-sensitivity lesson generalizes.

### 3. A foundation model for acute abdomen diagnosis stratification and triage on noncontrast CT (AbdomenNet)
*Nature Communications, 2026* — https://doi.org/10.1038/s41467-026-76634-w

**Why relevant:** AbdomenNet is externally validated on 2,528 patients from
three independent cohorts and assessed in a multi-reader, multi-case crossover
reader study, raising radiologists' mean AUROC from 0.812 to 0.924 and cutting
reading time — a strong template for how any chest X-ray triage model derived
from our cohort should ultimately be validated.

**What our data supports:** our cohort's mix of "No Finding" versus multiple
emergent-pattern labels (Pneumothorax, Effusion, Cardiomegaly) parallels the
risk-stratification/triage framing AbdomenNet targets, even though the organ
system and modality differ.

**What it cannot tell us:** AbdomenNet is trained and validated on abdominal
NCCT, not chest radiographs, so none of its reported AUROC/timing figures
apply to our data; it is included as a methodological benchmark for external
validation and reader-study design, not as a directly transferable model.

## Axes (recurring themes)

- **다기관 일반화 및 편향** (multi-institution generalization and bias) —
  RayDINO, Multicenter spine LLM study
- **희귀 소견 롱테일** (rare-finding long tail) — Multicenter spine LLM study
- **소량 라벨 적응** (adaptation with limited labels) — RayDINO
- **다기관 외부 검증 / 판독자 보조 임상 효용** (external validation and
  reader-assistance clinical utility) — AbdomenNet

## Note

These are automated literature recommendations only. All papers require
physician review before any clinical or research use, and none of them have
been validated on our specific cohort.
