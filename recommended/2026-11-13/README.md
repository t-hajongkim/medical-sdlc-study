# Paper recommendations — 2026-11-13

> 모든 추천은 의사의 검토가 필요합니다. (All recommendations require physician review.)

- **Research date:** 2026-11-13 (yesterday in Asia/Seoul; no `REQUESTED_DATE` given)
- **Actual search window:** 2026-10-15 to 2026-11-13 (30 days). The 1-day window returned nothing. The 7-day window returned one paper. The 30-day window returned 11 papers, of which only one was new and relevant.
- **Search query:** `chest radiograph deep learning`

## Cohort (aggregate only)

- 272 chest radiograph records from about 150 patients, across 5 institutions. All records are flagged synthetic.
- Views: PA and AP. Sex: roughly balanced. Adults of widely varying age (mean about 50).
- Labels: about 53% "No Finding". The rest are multi-label findings, mainly infiltration, atelectasis, nodule, effusion, fibrosis and pneumothorax. Many labels have very few cases.
- Image sizes and pixel spacing vary, consistent with multi-site, multi-device acquisition. Reports and clinical info exist as free text.

## Axes

`기관 간 일반화`, `판독 보고서 품질`

## Papers

### 1. Scaling medical imaging report generation with multimodal reinforcement learning (Nature Communications)
https://doi.org/10.1038/s41467-026-78767-4 — axes: 기관 간 일반화, 판독 보고서 품질

- **Why relevant:** Chest X-ray report generation with an external proprietary test set, subgroup analysis and expert radiologist validation. It reports fewer clinically significant errors, which is a clinician-facing readout rather than only a metric gain.
- **Our data:** Multi-institution, multi-device PA/AP radiographs with structured findings labels and free-text reports could be used to check whether generated reports reproduce the labelled findings at each site.
- **Cannot tell us:** Most gains are on benchmark text metrics (RadCliQ). The abstract gives no prospective or workflow outcome. Our cohort is small and synthetic, and rare labels are too sparse for stable per-finding estimates.

## Notes

- Fewer than 3 papers qualified after the 30-day window. The relevance standard was not lowered to reach 3.
- Already under `recommended/` and excluded: EVLF-FM, radiographer fracture detection, human oversight review, neonatal pneumoperitoneum automation bias, LV dysfunction on chest radiographs, and the text-guided image synthesis model.
- Excluded as not relevant to chest radiography: Chilean ultrasound delivery-date prediction, diabetic retinopathy graph model, scoliosis sensor suit, vertebra labeling.
- The abstract in `paper.json` is as published by the source, without the leading "Abstract" label.
