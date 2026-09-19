# Daily paper recommendations — 2026-09-18

**Research date:** 2026-09-18 (yesterday in Asia/Seoul at run time)
**Actual search window used:** 2026-08-19 to 2026-09-18 (30 days). The 1-day and
7-day windows ending 2026-09-18 returned zero results, so the search was widened
per protocol until at least 3 clinically relevant papers were found.
**Search queries used** (several broad queries were tried against the same
window because the source is matched on titles/abstracts):
- `chest X-ray multi-label deep learning diagnosis`
- `chest radiograph pneumonia deep learning diagnosis`
- `thoracic imaging AI external validation multicenter`

Note: several conference sources (MICCAI, IPMI, CVPR, NeurIPS, ICLR via arXiv)
returned HTTP 406/429 errors throughout this run and could not be queried;
retained papers below are all from the journal-side (OpenAlex) results, which
were reachable.

## Cohort description (aggregate only)

The masked `llm.hospital` view represents a chest radiograph cohort of 272
studies from 153 unique patients across 5 synthetic institutions (INST01–05,
48–62 studies each). Sex is balanced (136 male / 136 female), age ranges from 9
to 87 years (mean ≈ 51.5). Frontal views dominate (PA: 184, AP: 88). The most
common label is "No Finding" (145 studies), with the remaining studies showing
one or more of: Infiltration, Atelectasis, Nodule, Effusion, Fibrosis,
Pneumothorax, Cardiomegaly, Emphysema, Pleural Thickening, Mass, Edema,
Consolidation, and Hernia, frequently in combination (multi-label). All rows
are flagged `is_synthetic = true`.

Given this profile — a modest, multi-institution, multi-label chest/thoracic
imaging cohort with mixed frontal projections and a range of common findings —
the search targeted broad chest/thoracic imaging AI diagnosis and
generalization topics rather than a single disease.

## Retained papers

### 1. A multitask framework for automated multi-frame right upper quadrant ultrasound interpretation and clinical decision support
*Nature Communications, 2026, OpenAlex*
https://doi.org/10.1038/s41467-026-77498-w

**Why relevant:** Reports a vision-language agent trained at one institution and
externally validated at two independent institutions (University of Colorado,
Stanford) with clinician-blinded report evaluation and a concrete downstream
decision (cholecystectomy prediction) — the kind of multi-site, reader-study
evidence our cohort's multi-institution structure calls for, even though the
modality (RUQ ultrasound) differs from our chest radiographs.
**What our data supports:** Our cohort's own multi-institution design (5 sites)
makes the cross-site AUROC drop reported here (0.865 internal → 0.794/0.775
external) directly relevant to expectations for any AI tool deployed across
our institutions.
**What it cannot tell us:** It does not use chest radiographs, so its findings
classes and performance numbers cannot be transferred to our thoracic imaging
labels; it only informs expectations about generalization behavior.

### 2. Cohort-aware CT-first modeling for clinically oriented pulmonary lesion characterization and prognosis
*npj Digital Medicine, 2026, OpenAlex*
https://doi.org/10.1038/s41746-026-03159-3

**Why relevant:** Addresses pulmonary lesion/nodule characterization — a
finding present in our cohort (Nodule, Mass) — using a large, harmonized,
multi-cohort dataset (28,105 cases) with internal and independent external
validation, explicit calibration, and a stated need for prospective multicenter
validation, matching a reader/clinician-actionable evidence bar.
**What our data supports:** Our cohort contains a small number of Nodule/Mass
cases, so this paper is relevant background for how a lesion-characterization
AI tool might be evaluated and calibrated if applied to our nodule cases, and
what performance degradation to expect externally (internal AUC 0.955–0.978 vs
external Dice 0.878, C-index 0.709→0.857).
**What it cannot tell us:** It uses CT (with optional PET), not the plain
chest radiographs in our cohort, and our cohort's nodule/mass count is too
small to validate or replicate any of its cohort-specific figures.

### 3. On-premise medical AI agents for reliable clinical decision-making
*Nature Medicine, 2026, OpenAlex*
https://doi.org/10.1038/s41591-026-04609-x

**Why relevant:** Evaluates an on-premise, institutionally deployable clinical
AI agent with decision-time reliability/uncertainty estimation on
MIMIC-IV-derived multi-disease diagnostic tasks — directly useful for how a
multi-institution deployment (like our 5-site cohort) could triage
higher-confidence AI outputs for autonomous handling versus deferring
lower-confidence cases for radiologist review.
**What our data supports:** Our cohort's multi-label, multi-finding structure
(many co-occurring diagnoses per study) mirrors the multi-disease diagnostic
task studied here, so its reliability/consistency framework is a plausible
fit for triaging chest radiograph findings across our institutions.
**What it cannot tell us:** The underlying benchmarks are MIMIC-IV
ICU/EHR-based diagnostic tasks, not imaging-based diagnosis, so its accuracy
and reliability figures do not directly transfer to radiograph interpretation
and would need dedicated imaging-specific validation.

## Axes (검토 축)

- **기관 간 일반화** (cross-institution generalization): papers 1 and 2 — both
  report performance drops or calibration needs when moving from an internal
  cohort to independent external sites, directly relevant to our 5-institution
  cohort.
- **임상 의사결정 지원** (clinical decision support): papers 1 and 3 — both
  connect model output to a concrete downstream clinical action or triage
  decision rather than classification metrics alone.
- **결절/병변 특성화** (nodule/lesion characterization): paper 2 — matches the
  Nodule/Mass findings present in our cohort.
- **신뢰도/불확실성 추정** (reliability/uncertainty estimation): paper 3 —
  proposes decision-time consistency signals to select cases for autonomous
  handling versus review.

## Physician review notice

These recommendations are automatically generated from a broad literature
search and cohort-level summary statistics only. They are **not** a
substitute for clinical judgment. Please review each paper's methodology,
population, and applicability before using it to inform patient care or
further study design.
