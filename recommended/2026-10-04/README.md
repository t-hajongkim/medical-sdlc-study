# 2026-10-04 논문 추천

- **연구 기준일**: 2026-10-04 (Asia/Seoul 기준 어제)
- **실제 검색 창**: 2026-10-04 단일일(0건) → 7일(2026-09-28~10-04, 2건, 모두 부적합) → **2026-09-05~2026-10-04 (30일)**
- **검색 질의**: `chest radiograph deep learning` (30일 창에서는 보완 질의 `chest X-ray`, `thoracic imaging artificial intelligence`도 사용)
- 목표 3편에 미달하여 2편만 채택함(관련성 기준은 낮추지 않음). 일부 소스는 간헐적으로 결과가 불완전하게 반환되었음(CXR-LT 2026 챌린지 논문은 반복 검색에도 본문을 확보하지 못해 평가하지 못함).

## 코호트 요약 (masked `llm.hospital` 뷰, 집계 값만)

- 흉부 단순촬영(CXR) 272건, 고유 환자 약 150명, 5개 기관·9개 장비
- 연령 9–87세(평균 약 51세), 성별 균형, PA 약 2/3, AP 약 1/3
- 소견 라벨: 무소견 약 53%, 그 외 Infiltration, Atelectasis, Nodule, Effusion 등 다중 라벨 포함
- 합성 데이터로 표시됨

## 채택 논문

### 1. Anatomy-Structured Hierarchical MIL for Weakly-Supervised Thoracic Disease Detection in Chest X-rays
- 링크: http://arxiv.org/abs/2609.33520v1 (MICCAI, arXiv)
- **관련성**: 영상 단위 라벨만으로 심장·폐 해부학 사전지식을 이용해 병변 위치 근거 지도를 만드는 방법. CXR8 및 MIMIC-CXR 교차 도메인 평가가 포함됨.
- **우리 데이터가 뒷받침하는 점**: 우리 데이터도 영상 단위 다중 라벨(Infiltration, Nodule, Effusion 등)만 있고 박스 주석이 없어 약지도 설정과 일치하며, 다기관·PA/AP 혼재로 도메인 이동 평가가 가능함.
- **알 수 없는 점**: 환자 코호트 기반 임상 결과나 판독자 연구가 없는 방법론 논문임. 라벨 외 위치 정답이 없는 우리 데이터로는 국소화 정확도를 검증할 수 없음.

### 2. Learning to Defer with Guidance on Real World Medical Data
- 링크: http://arxiv.org/abs/2609.26384v1 (MICCAI, arXiv)
- **관련성**: 사람 판독 라벨이 있는 CXR 데이터(Collab-CXR, VinDr-CXR, CheXpert)에서 AI 단독, 의사 단독, 지연(defer)·AI 가이드 병용을 비교함. 판독자 주석이 있는 실제 데이터 평가라는 점에서 임상 활용성이 상대적으로 높음.
- **우리 데이터가 뒷받침하는 점**: 무소견 비율이 높고 소견 분포가 불균형하여 선별·위임 정책이 실질적 업무량에 영향을 줄 수 있음. 판독 상태·판독의 정보 필드가 있어 후속 설계 시 참고 가능함.
- **알 수 없는 점**: 우리 데이터에는 복수 판독자의 독립 주석이 없어 L2D 재현이 불가하며, 공개 데이터 결과가 우리 기관 환경으로 일반화되는지는 미확인임. 전향적 임상 연구가 아님.

## 제외 사유 요약
CT 중심(CT 비전-언어 모델, 점액전 판독), ICU 사망 예측용 CXR-EHR 모델(GLR-MM; 우리 데이터에 EHR/결과 변수 없음), ECG, 교육·서지 논문, 기존 추천과 중복된 논문은 제외함.

> 본 추천은 자동 검색 결과이며 반드시 의사의 검토가 필요합니다.
