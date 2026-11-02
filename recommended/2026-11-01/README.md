# Paper recommendations — 2026-11-01

> 모든 추천은 의사의 검토가 필요합니다. (All recommendations require physician review.)

- **Research date:** 2026-11-01 (yesterday in Asia/Seoul; no `REQUESTED_DATE` given)
- **Actual search window:** 2026-10-02 to 2026-11-01 (30 days). The 1-day window returned nothing, and the 7-day window yielded fewer than 3 new qualifying papers.
- **Search query:** `chest radiograph deep learning`

## Cohort (aggregate only)

- 272 chest radiograph records from 153 patients, across 5 institutions and 9 devices. All records are flagged synthetic.
- Views: PA and AP. Sex: roughly balanced. Age spans adolescents to the late 80s (mean about 50).
- Labels: about 53% "No Finding". The rest are multi-label findings, mainly infiltration, atelectasis, nodule, effusion, fibrosis and pneumothorax. Many labels have very few cases.
- Image sizes and pixel spacing vary, which is consistent with multi-site, multi-device acquisition.

## Axes

`설명가능성`, `기관 간 일반화`, `판독자-AI 상호작용`, `데이터 부족·합성 데이터`

## Papers

### 1. A clinical multimodal vision language foundation model with fine-grain explainability (Nature Medicine)
https://doi.org/10.1038/s41591-026-04655-5 — axes: 설명가능성, 기관 간 일반화

- **Why relevant:** Includes pulmonology and radiology, with external validation and human rating of the explanations. It could serve as a zero-shot or few-shot baseline for multi-label chest X-ray findings, with visual grounding that a clinician can check.
- **Our data:** Multi-label findings from 5 institutions allow zero-shot testing and a check that grounding matches the labelled finding.
- **Cannot tell us:** Chest X-ray performance on its own is not reported in the abstract. No prospective study or clinical outcome. The authors state that further validation in diverse settings is needed. Our cohort is small and synthetic, and rare labels are too sparse for stable estimates.

### 2. Radiographer fracture detection with and without AI assistance in prospective emergency department use (npj Digital Medicine)
https://doi.org/10.1038/s41746-026-03313-x — axes: 판독자-AI 상호작용, 기관 간 일반화

- **Why relevant:** Prospective, real-world, paired-read evidence with a radiologist reference standard. It is the most clinically actionable paper here. Standalone AI was weaker than the readers, and the gain was small and came from complementary errors. 8.8% of examinations returned no or incomplete AI output.
- **Our data:** Includes emergency-department visits and AP views, where subtle findings and operational failures matter. It also lets us plan a similar paired-read design.
- **Cannot tell us:** It covers musculoskeletal fracture, not chest findings. Single site, no downstream outcomes, and few behavioural events.

### 3. A generalist model for diverse text-guided medical image synthesis (npj Digital Medicine)
https://doi.org/10.1038/s41746-026-03381-z — axes: 데이터 부족·합성 데이터

- **Why relevant:** Our cohort has many rare labels with very few cases. Synthetic augmentation for data-limited classifiers is therefore a plausible option. The model is open access and trained on public data.
- **Our data:** Rare-label sparsity and per-institution imbalance support the augmentation motivation.
- **Cannot tell us:** Purely methodological, with no clinical readout or patient cohort evidence. The abstract does not report chest-specific gains. Our records are already synthetic, so any benefit for real-patient generalization is not shown.

## Notes

- Papers already under `recommended/` were excluded, including the LV dysfunction, osteoporosis, neonatal and oversight papers, and the confidence-interval study.
- Excluded as not relevant: scoliosis sensor suit, vertebra labeling, code-sharing scoping review.
- Abstracts in `paper.json` are as published by the source.
