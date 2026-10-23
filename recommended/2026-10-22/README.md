# 논문 추천 — 2026-10-22

- 연구 날짜: 2026-10-22 (`REQUESTED_DATE` 미지정, 서울 기준 어제)
- 실제 검색 창: 1일(결과 없음) → 7일 → 30일(2026-09-22 ~ 2026-10-22)
- 검색어: `chest radiograph deep learning`
- 30일 창에서 새로 적합한 논문은 2편뿐이었습니다. 3편이라는 목표를 채우기 위해 관련성 기준을 낮추지 않았습니다.

> 모든 추천은 의사의 검토가 필요합니다.

## 코호트 요약 (집계 수치만)

마스킹된 `llm.hospital` 뷰의 흉부 X-ray 코호트, 272건. 약 53%가 "No Finding"이며 나머지는 침윤, 무기폐, 결절, 흉수, 섬유화, 기흉, 심비대 등 ChestX-ray14 계열 다중 라벨입니다. PA·AP 촬영이 섞여 있고 성인 위주(대략 9–87세)이며 남녀 모두 포함됩니다. 여러 기관 코드와 응급·심장내과·호흡기내과·내과·영상의학과 진료과가 있습니다. 영상, 라벨, 기본 인구통계만 있고 심초음파나 추적 결과는 없습니다.

## 1. Interpretable Deep Learning for Opportunistic Screening of Left Ventricular Dysfunction Using Chest Radiographs

- 링크: https://doi.org/10.1148/ryai.260161 (Radiology: Artificial Intelligence, 2026-10-21)
- 관련성: 흉부 X-ray만으로 좌심실 박출률 저하를 선별하는 모델이며, 3개 외부 코호트에서 검증했고 TTE 절감 효과와 놓친 사례 부담까지 보고해 임상 판단에 쓸 수 있습니다.
- 우리 데이터의 근거: 흉부 X-ray 코호트이고 심비대·부종·흉수 라벨이 일부 있으며 심장내과 진료 건이 있습니다. 여러 기관 코드로 기관 간 일반화를 확인할 여지가 있습니다.
- 한계: 우리 데이터에는 LVEF나 심초음파 기준값이 없어 이 모델을 검증할 수 없습니다. 272건으로는 건강검진 수준의 낮은 유병률을 재현하지 못합니다.

## 2. Expertise modulates automation bias and sentinel behavior in human–AI collaborative diagnosis of neonatal pneumoperitoneum

- 링크: https://doi.org/10.1038/s41746-026-03399-3 (npj Digital Medicine, 2026-10-20)
- 관련성: 판독자 연구로, 전문성에 따라 AI 오류를 얼마나 수용하는지 보여줍니다. AI 보조 판독을 도입할 때 읽기 연구 설계에 참고할 수 있습니다.
- 우리 데이터의 근거: 응급·영상의학과 등 판독 환경이 다양한 방사선 영상 코호트이고 판독문과 판독 상태 정보가 있어 판독자 연구를 설계할 수 있습니다.
- 한계: 대상이 신생아 복부 X-ray이고 판독자가 3명인 가설 생성 수준의 연구입니다. 우리 코호트는 성인 흉부 영상이므로 결과를 직접 적용할 수 없습니다.
