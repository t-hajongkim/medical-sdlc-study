# Daily Paper Recommendations — 2026-09-03

## Search details

- **Research date:** 2026-09-03 (yesterday in Asia/Seoul relative to workflow run)
- **Search window used:** 2026-08-04 to 2026-09-03 (30 days). The 1-day window (2026-09-03) and the 7-day window (2026-08-28 to 2026-09-03) each returned 0–1 candidates, so the search was widened per the escalation rule until at least 3 clinically relevant papers were found.
- **Search queries issued (title/abstract match):**
  - "chest radiograph deep learning multi-institution generalization"
  - "chest X-ray classification reader study external validation"
  - "pneumothorax nodule detection chest X-ray AI"
  - "thoracic disease multi-label classification chest imaging" (rate-limited, no results)
  - "chest X-ray disease classification deep learning cohort"
  - "domain shift label noise medical image segmentation robustness"
  - "radiologist AI assistance reader study diagnostic accuracy" — this query surfaced the 3 papers retained below.

## Cohort description (aggregate only)

The masked `llm.hospital` view covers 272 chest radiograph studies from 153 patients across 5 institutions (INST01–INST05, roughly 48–62 studies each). Sex is balanced (136 M / 136 F), age ranges 9–87 years (mean ≈ 51.5), and views are mostly PA (184) with some AP (88). The dominant finding label is "No Finding" (145), followed by Infiltration (21), Atelectasis (16), Nodule (7), Fibrosis (6), Effusion (6), Cardiomegaly (5), Pneumothorax (5), and various multi-label combinations (e.g. Effusion+Infiltration, Effusion+Pneumothorax). All rows are flagged as synthetic. No patient-level values are reported here.

Given the multi-institution structure, modest cohort size, and long-tailed, often multi-label thoracic findings, the most clinically actionable literature is work that reports **external, multi-center validation** and/or **reader studies quantifying how AI assistance changes physician diagnostic accuracy or reading time** — rather than single-center methodological advances alone.

## Retained papers

None of the 5 prior newsletters ("2026-08-20", "2026-08-23", "2026-09-02") already covered the following three, and no purely chest-X-ray-specific paper met the bar this cycle within 30 days — but all three retained papers directly address the two axes below (multi-institution external validation and AI-assisted reader performance), which generalize to how our multi-institution chest X-ray cohort would need to be validated and deployed.

### 1. Interpretable deep learning for three-stage focal liver lesion diagnosis on non-contrast MRI: a multicenter, prospective study
- **Venue:** npj Digital Medicine (2026)
- **Why relevant:** A 9-institution, 12,823-patient multicenter cohort with a 13-radiologist multireader-multicase study quantifying AI-assisted gains in accuracy and reading time — directly modeling the kind of external validation and reader-impact evidence our 5-institution chest X-ray cohort would need before any triage tool is deployed.
- **Supported by our data:** Our cohort's cross-institution structure (5 sites, uneven case counts) makes site-level generalization and reader-time effects a first-order concern, mirrored in this study's design.
- **What it cannot tell us:** It studies liver MRI, not chest radiographs, so its specific accuracy/AUC numbers do not transfer; it only supports the validation *methodology*, not our disease labels.
- **Link:** https://doi.org/10.1038/s41746-026-03032-3

### 2. Lightweight non-contrast CT-based multimodal AI for subtype classification of hepatic cystic echinococcosis in resource-limited clinical settings
- **Venue:** npj Digital Medicine (2026)
- **Why relevant:** Explicit internal-vs-external (tertiary vs. county-hospital) validation plus a reader study showing AI-assisted macro-AUC gains at both the developing and external sites — a template for assessing whether a chest X-ray classifier trained at one institution keeps its accuracy at another.
- **Supported by our data:** With imbalanced findings (few Nodule/Fibrosis/Pneumothorax cases) split across 5 institutions, subtype-level performance in a small-numbers, multicenter setting is analogous to our label distribution.
- **What it cannot tell us:** Population (hepatic cystic echinococcosis, largely regional), imaging modality, and CE1–CE5 staging task are unrelated to thoracic findings; only the study design transfers.
- **Link:** https://doi.org/10.1038/s41746-026-03150-y

### 3. AgentDS-BUS: a fine-tuning-free agentic breast ultrasound malignancy classification framework with decoupled segmentation and feature analysis
- **Venue:** npj Digital Medicine (2026)
- **Why relevant:** Evaluates a foundation-model-based pipeline across 7 independent public breast-ultrasound benchmarks (cross-dataset acquisition shift), directly analogous to the cross-institution acquisition variability (different devices/views across INST01–05) present in our cohort.
- **Supported by our data:** Our cohort mixes AP/PA views and 5 device/institution combinations, so robustness to acquisition variability without per-site fine-tuning is a practically relevant property.
- **What it cannot tell us:** No physician reader study and a different modality/organ (breast ultrasound vs. chest radiograph); AUROC/AUPRC values are not transferable to thoracic disease detection.
- **Link:** https://doi.org/10.1038/s41746-026-03144-w

## Axes

- **다기관 외부검증** (multi-institution external validation): all three papers.
- **AI 보조 판독 성능 개선** (AI-assisted reader performance improvement): papers 1 and 2.

## Physician review notice

These recommendations are automatically generated from a literature search matched against aggregate cohort characteristics. They require review by a physician or clinical researcher before any conclusions are drawn or acted upon; none of the papers were validated on this specific dataset.
