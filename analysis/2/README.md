# Deep dive: CLEAR — Nodule 하위군 거짓음성 검토 (issue #2)

- 논문: [CLEAR — Nature Biomedical Engineering, 2026](https://doi.org/10.1038/s41551-026-01741-4) (`recommended/2026-08-20/clear-auditable-radiology-foundation-model/paper.json`)
- 승인된 계획: [`analysis/2/plan.md`](./plan.md) (PR #3에서 병합됨)
- 대상 이슈: [#2](https://github.com/t-hajongkim/medical-sdlc-study/issues/2) — "결절(Nodule) 증례가 적은 코호트에서도 이 방법이 통할까요? 거짓음성이 걱정입니다. Nodule 하위군의 실제 크기와 PA/AP 뷰 구성이 검증 코호트와 얼마나 다른지 짚어 주세요."

## 요약 표 — Nodule 하위군 vs 코호트 전체

| 항목 | 값 | 근거 쿼리 |
|---|---|---|
| 전체 연구 수 | 272건 | `SELECT count(*) FROM llm.hospital` |
| 전체 환자 수 | 153명 | `SELECT count(DISTINCT patient_key) FROM llm.hospital` |
| Nodule 포함 연구 (다중라벨 포함) | 12건 (4.4%) | `SELECT count(*) FROM llm.hospital WHERE findings_label ~ 'Nodule'` |
| 순수 `Nodule` 라벨 | 7건 | `SELECT count(*) FROM llm.hospital WHERE findings_label = 'Nodule'` |
| Nodule 하위군 성별 | F 7명(평균 51.9세), M 5명(평균 58.8세) | `SELECT sex, count(*), round(avg(age),1) FROM llm.hospital WHERE findings_label ~ 'Nodule' GROUP BY sex` |
| Nodule 하위군 연령 범위 | 32–77세 (n=12) | `SELECT min(age), max(age), count(*) FROM llm.hospital WHERE findings_label ~ 'Nodule'` |
| Nodule 하위군 뷰 구성 | PA 10 / AP 2 (83% / 17%) | `SELECT view_position, count(*) FROM llm.hospital WHERE findings_label ~ 'Nodule' GROUP BY view_position` |
| 코호트 전체 뷰 구성 | PA 184 / AP 88 (68% / 32%) | `SELECT view_position, count(*) FROM llm.hospital GROUP BY view_position` |
| 코호트 전체 성별 | M 136 / F 136 | `SELECT sex, count(*) FROM llm.hospital GROUP BY sex` |
| Nodule 하위군 기관-장비 조합 | 11개 조합 / 12건 (거의 1:1) | `SELECT institution_code, device_id, count(*) FROM llm.hospital WHERE findings_label ~ 'Nodule' GROUP BY institution_code, device_id` |
| 픽셀 간격 (평균) | Nodule 하위군 0.1639 vs 전체 0.1591 | `SELECT round(avg(pixel_spacing_x)::numeric,4) FROM llm.hospital [WHERE ...]` |

<details>
<summary>Raw query outputs</summary>

```
-- 전체 findings_label 분포 (상위 항목)
No Finding|145
Infiltration|21
Atelectasis|16
Nodule|7
Effusion|6
Fibrosis|6
Pneumothorax|5
Effusion|Infiltration|5
Cardiomegaly|5
... (총 46개 조합, 롱테일)

-- Nodule을 포함하는 조합
Nodule|7
Atelectasis|Nodule|1
Effusion|Infiltration|Nodule|1
Effusion|Infiltration|Nodule|Pleural_Thickening|1
Effusion|Nodule|1
Fibrosis|Nodule|1
(합계 12건)

-- Nodule 하위군 성별/연령
F|7|51.9
M|5|58.8

-- Nodule 하위군 연령 범위
min=32, max=77, n=12

-- Nodule 하위군 뷰 구성
AP|2
PA|10

-- 코호트 전체 뷰 구성
AP|88
PA|184

-- Nodule 하위군 기관-장비 조합
INST01|DEV05|1
INST01|DEV06|2
INST01|DEV09|1
INST02|DEV04|1
INST02|DEV09|1
INST03|DEV09|1
INST04|DEV05|1
INST04|DEV09|1
INST05|DEV02|1
INST05|DEV03|1
INST05|DEV07|1
```

</details>

## PA vs AP 뷰 구성 비교 (figure.svg)

`analysis/2/figure.svg` 참조 — Nodule 하위군(n=12)은 PA 83% / AP 17%, 코호트 전체(n=272)는 PA 68% / AP 32%로, Nodule 하위군이 상대적으로 PA에 더 치우쳐 있습니다. AP 촬영은 기하학적 확대/왜곡이 달라 작은 결절의 가시성에 영향을 줄 수 있다는 점에서, 이 차이는 참고할 만하지만 n=12는 통계적 근거로는 너무 작습니다.

## 논문이 보고한 것 vs 우리 데이터가 보여주는 것 vs 우리가 추론한 것

**논문이 보고한 것** (abstract 및 `paper.json`, [DOI](https://doi.org/10.1038/s41551-026-01741-4)):
- 0.87M개 이상의 이미지-리포트 쌍, 239,391명 환자로 학습.
- 미국·유럽·아시아의 4개 대규모 physician-annotated 외부 검증 코호트에서 state-of-the-art 분류 성능.
- 모든 예측을 임상 개념 가중치로 분해 가능 (auditable), zero-shot 병리 탐지, 방사선학적 confounder 식별, concept bottleneck 모델 생성 지원.
- **abstract 수준에서 확인 불가**: 병리별(예: Nodule) 유병률, 외부 검증 코호트별 크기, 인구통계, 뷰 포지션 구성, 정량적 민감도/거짓음성률 수치 — 이들은 본문/보충자료에 있을 가능성이 높으나 이번 분석에서는 abstract와 `paper.json` 요약만 사용했습니다.

**우리 데이터가 보여주는 것** (`llm.hospital`, 위 쿼리 결과):
- 272건 중 Nodule을 포함하는 연구는 12건(4.4%)뿐이고 순수 `Nodule` 라벨은 7건입니다.
- Nodule 하위군은 PA 뷰가 83%로 코호트 전체(68%)보다 높습니다.
- Nodule 하위군의 기관-장비 조합은 11개로 12건에 거의 1:1 대응하여, 특정 장비에 쏠린 패턴은 보이지 않습니다.
- 픽셀 간격은 Nodule 하위군(0.1639mm)과 전체(0.1591mm)가 비슷해 해상도 자체가 큰 교란요인은 아닌 것으로 보입니다.

**우리가 추론한 것** (가설 수준):
- CLEAR의 개념 기반 감사 접근은 양성 사례가 극히 적은(n=12) 상황에서 전통적 분류기 재학습보다 데이터 효율적일 잠재력이 있습니다.
- 다만 논문의 실제 외부 검증 코호트가 우리와 유사한 정도의 Nodule 유병률·PA/AP 비율을 가졌는지 확인할 수 없으므로, 이 잠재력이 실제로 우리 코호트에 전이될지는 **미지수**입니다.
- Nodule 하위군의 PA 편향(83% vs 68%)이 거짓음성 위험에 실제로 영향을 미치는지는 이번 분석만으로는 판단할 수 없습니다 — 모델을 우리 이미지에 실제로 구동해 보지 않았기 때문입니다.

## Limitations

- **모델 미실행**: CLEAR를 우리 이미지에 대해 zero-shot 추론으로 실행하지 않았으므로, 로컬 민감도·특이도·거짓음성률은 전혀 산출하지 못했습니다. 이번 분석은 순수 데이터 특성 비교입니다.
- **논문 원문 미확보**: abstract와 `paper.json` 요약만 사용했고, 본문·보충자료(병리별 유병률, 코호트별 크기, 인구통계, 정량적 성능표)는 확인하지 못했습니다. 위 "논문이 보고한 것" 항목 중 다수가 실제로는 본문에 존재할 수 있습니다.
- **표본 크기**: Nodule 하위군 n=12(순수 라벨 n=7)는 통계적 검정력이 매우 낮습니다. PA/AP 비율 차이(83% vs 68%)나 기관-장비 분포는 가설 생성 수준으로만 해석해야 하며, 유의성 검정은 수행하지 않았습니다.
- **다기관 규모 격차**: 논문은 미국·유럽·아시아 4개국 규모의 외부 검증인 반면, 우리는 5개 기관코드(INST01–05)로 이루어진 훨씬 작은 단일 권역 코호트입니다. 지역적 일반화 가능성 비교는 이 분석 범위를 벗어납니다.
- **라벨 정의 불일치 가능성**: 우리 `findings_label`은 리포트 기반 다중 라벨 체계이나, 이것이 CLEAR가 학습에 사용한 개념 온톨로지와 정확히 대응하는지는 검증하지 않았습니다.
