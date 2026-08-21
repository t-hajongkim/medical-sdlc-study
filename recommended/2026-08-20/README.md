# Daily Paper Recommendations — 2026-08-20

**Research date:** 2026-08-20 (yesterday in Asia/Seoul)
**Actual search window used:** 2026-07-22 to 2026-08-20 (30-day window; the 1-day and 7-day
windows returned no results)
**Search query:** `chest X-ray deep learning classification`

## Cohort snapshot (aggregate only, no patient-level values)

- 272 chest X-ray studies from 153 masked patients.
- Sex nearly balanced (136 M / 136 F); age range 9–87 years, mean ≈ 51.5.
- View position: 184 PA, 88 AP.
- Findings label distribution (top labels): "No Finding" (145), Infiltration (21),
  Atelectasis (16), Nodule (7), Fibrosis (6), Effusion (6), Cardiomegaly (5),
  Effusion+Infiltration (5), Pneumothorax (5), Emphysema (4), plus several
  multi-label combinations (Atelectasis/Effusion/Infiltration/Consolidation/
  Emphysema/Pleural_Thickening/Pneumothorax) each with small counts.
- This is a modest, multi-pathology plain chest radiograph cohort typical of a
  screening/ward population, with report text and clinical info fields available
  per study.

## Retained papers

### 1. CLEAR: an auditable foundation model for radiology grounded in clinical concepts
*Nature Biomedical Engineering, 2026* — https://doi.org/10.1038/s41551-026-01741-4

**Why relevant:** CLEAR is trained on ~0.87M chest X-ray/report pairs and externally
validated on four large, physician-annotated cohorts across the US, Europe, and Asia
for exactly the kind of multi-label chest pathology classification present in our
data (Infiltration, Atelectasis, Effusion, Nodule, Cardiomegaly, Pneumothorax, etc.).
**What our data supports:** our cohort's multi-label findings distribution and mixed
PA/AP views mirror the classification targets CLEAR was validated against, and its
concept-based explanations could help audit predictions against the report_text/
clinical_info fields we hold.
**What it cannot tell us:** our cohort is far smaller (153 patients) than CLEAR's
training/validation sets, so device- or institution-specific calibration would still
be needed before any local deployment.

### 2. Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
*npj Digital Medicine, 2026* — https://doi.org/10.1038/s41746-026-03051-0

**Why relevant:** CF2Seg turns free-text chest X-ray findings into spatial
localization/segmentation, evaluated on a 53,386-exam multi-institution benchmark
under distribution shift and annotation scarcity — directly applicable to using our
report_text alongside images without pixel-level labels.
**What our data supports:** our dataset has report/clinical-info text but no
segmentation masks, matching the exact "reports only, no pixel annotations" gap this
paper addresses; our small annotation set is the "scarcity" regime the paper stress-
tests.
**What it cannot tell us:** it does not establish performance for our specific device/
institution mix, and needs independent evaluation before being used to generate
lesion-burden estimates from our reports.

### 3. UniMedDiff: a knowledge-enhanced diffusion model for medical image generation from clinical reports
*npj Digital Medicine, 2026* — https://doi.org/10.1038/s41746-026-03135-x

**Why relevant:** UniMedDiff synthesizes chest X-rays for 11 pulmonary pathologies
from clinical reports and shows that augmenting with only 1% real data approaches
full-data performance on downstream classification — directly relevant given our
modest cohort size (153 patients, many low-count pathology labels like Nodule,
Fibrosis, Pneumothorax).
**What our data supports:** our long tail of rare multi-label findings (e.g., single-
digit counts for several combinations) is precisely the low-data regime this method
targets for augmentation.
**What it cannot tell us:** synthetic augmentation quality/faithfulness for our
specific label distribution and imaging protocol (PA/AP mix, pixel spacing) has not
been separately verified and would need local validation before use in model
training.

## Axes (recurring themes)

- **다기관 외부 검증** (multi-institution external validation) — CLEAR, CF2Seg
- **소견 기반 국소화/설명가능성** (report/finding-grounded localization and
  explainability) — CLEAR, CF2Seg, UniMedDiff
- **데이터 부족/증강** (data scarcity and augmentation) — UniMedDiff

## Note

These are automated literature recommendations only. All papers require physician
review before any clinical or research use, and none of them have been validated on
our specific cohort.
