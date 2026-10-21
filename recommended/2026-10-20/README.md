# 논문 추천 — 2026-10-20

> ⚠️ 모든 추천은 의사의 검토가 필요합니다.

- **조사 기준일**: 2026-10-20 (Asia/Seoul 기준 어제)
- **실제 검색 구간**: 2026-09-21 ~ 2026-10-20 (당일 → 7일 → 30일 순으로 확대; 당일 결과 없음, 30일 구간에서 신규 적합 논문 2편)
- **검색어**: `chest radiograph deep learning`

## 코호트 요약 (집계만)

- 흉부 X선 영상 272건, 5개 기관, AP/PA 촬영 혼재.
- 연령 9–87세, 여성 약 50%.
- 소견 라벨: "No Finding" 약 53%, 나머지는 단일·복수 라벨(Infiltration, Atelectasis, Effusion, Fibrosis, Nodule, Pneumothorax 등). 희귀 라벨은 각 수 건 수준.

## 선정 논문

### 1. Repurposing adult AI radiograph models for neonatal care through continual learning (Nature Biomedical Engineering)
- 링크: https://doi.org/10.1038/s41551-026-01812-6
- **관련성**: 기관당 50장 정도의 소량 데이터로 데이터 공유 없이 순차 재학습하는 다기관 연속학습을 평가. 우리 데이터도 5개 기관·소규모라는 점에서 기관 간 적응 전략 참고 가능.
- **우리 데이터의 근거**: 5개 기관, 기관당 평균 약 50장 규모.
- **한계**: 신생아 기관내삽관 위치 평가 과제이며 우리 데이터는 최소 연령 9세로 신생아가 없고 소견 분류 과제임. 결과를 직접 적용할 수 없음.

### 2. Performance uncertainty in medical image analysis: A large-scale investigation of confidence intervals (Medical Image Analysis)
- 링크: https://doi.org/10.1016/j.media.2026.104349
- **관련성**: 신뢰구간 신뢰도가 표본 수, 지표, 집계 방식(macro/micro)에 따라 달라짐을 분석. 272장·다중 라벨·희귀 라벨 소수라는 우리 데이터에서 성능 추정의 정밀도를 해석하는 데 유용.
- **우리 데이터의 근거**: 희귀 라벨이 수 건뿐이라 macro 지표 CI가 불안정할 가능성.
- **한계**: 임상 코호트 결과가 아닌 방법론 연구이며 질환별 임상 판단 근거는 제공하지 않음.

## 제외 사유

나머지 검색 결과는 이미 `recommended/`에 있거나(CXR 골다공증, CXR 파운데이션 모델 리뷰) 흉부 X선과 무관(척추 라벨링, CT 모델, 코드 공유, 디지털 트윈 교육)하여 제외했습니다. 적합 논문이 3편 미만이지만 기준을 낮추지 않았습니다.
