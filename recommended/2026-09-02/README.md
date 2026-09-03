# Daily paper recommendations — 2026-09-02

**Research date:** 2026-09-02 (Asia/Seoul yesterday)

**Search windows used (widened progressively because the 1-day and 7-day windows
returned fewer than 3 clinically relevant papers):**
- 2026-09-02 → 2026-09-02: 0 results
- 2026-08-27 → 2026-09-02: 2 results, not enough clinically actionable hits
- 2026-08-03 → 2026-09-02 (30 days): used for final selection

**Search queries used:** "chest radiograph deep learning diagnosis",
"chest X-ray multi-label classification reader study",
"thoracic imaging AI radiologist external validation"

## Cohort summary (masked `llm.hospital` view)

- 272 chest radiograph studies, roughly balanced by sex (136 M / 136 F), mean age
  ~49 (M) / ~54 (F).
- View position skewed toward PA (184) over AP (88).
- Findings label distribution dominated by "No Finding" (145), followed by
  Infiltration (21), Atelectasis (16), Nodule (7), Fibrosis (6), Effusion (6),
  Cardiomegaly (5), Pneumothorax (5), and various multi-label combinations
  (e.g., Effusion+Infiltration, Atelectasis+Infiltration).
- This is a modest single/limited-institution frontal chest radiograph cohort
  with a long tail of low-prevalence findings — exactly the setting where
  cross-institutional generalization and rare-finding precision matter most.

## Retained papers

### 1. Impact of Commercial Artificial Intelligence on Radiologist Reading Time for Pulmonary Nodule Evaluation at Chest CT (Radiology)
Real-world implementation study showing an AI nodule-assessment tool reduced
radiologist reading time in clinical practice. Relevant because our cohort
contains nodule cases (7 single-label + several in combination) and any
nodule-focused workflow tool has direct bearing on how such findings would be
triaged locally. It cannot tell us whether reading-time gains generalize to a
plain-radiograph (rather than CT) workflow, or to our specific low-nodule-
prevalence, small cohort.
- Link: https://doi.org/10.1148/radiol.260484

### 2. A foundation model for acute abdomen diagnosis stratification and triage on noncontrast CT (Nature Communications)
Large-scale multi-reader, multi-case, externally validated (2528 patients,
3 independent cohorts) triage foundation model, with a measured effect on
radiologist AUROC and reporting turnaround. It is the strongest methodological
exemplar of external validation and reader-study design among this window's
candidates — a template for how our own low-prevalence-finding cohort would
need to be validated before any AI triage tool could be trusted. It cannot
directly inform chest radiograph interpretation since its target organ system
and modality (abdominal NCCT) differ from our cohort.
- Link: https://doi.org/10.1038/s41467-026-76634-w

### 3. Multicenter evaluation of four large language models for automated spine imaging diagnosis (npj Digital Medicine)
Multi-institution (3 hospitals), multi-model cohort study reporting how
diagnostic precision degrades for low-prevalence conditions under cross-
institutional testing — directly analogous to our cohort's long tail of rare
labels (Nodule, Fibrosis, Pneumothorax, multi-label combinations) where a
single-institution model's precision on rare findings is unverified. It cannot
tell us how these findings transfer from spine radiology reports/LLMs to
image-based chest radiograph classifiers.
- Link: https://doi.org/10.1038/s41746-026-03133-z

## Axes

- **기관 간 일반화** (cross-institutional generalization): AbdomenNet external
  cohorts, spine-imaging LLM multicenter validation.
- **저빈도 질환 진단 정확도** (low-prevalence finding precision): spine-imaging
  LLM precision drop on rare conditions, directly mirrors our long-tail label
  distribution.
- **판독자 성능 평가** (reader-study design): AbdomenNet multi-reader
  multi-case crossover study.
- **임상 워크플로 영향 / 판독 효율성** (clinical workflow / reading efficiency):
  pulmonary nodule CT reading-time study.

## Note

These are automated literature suggestions based on masked cohort-level
statistics only. **All recommendations require physician review** before any
clinical or research action is taken.
