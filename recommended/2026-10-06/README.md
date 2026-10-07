# 2026-10-06 논문 추천

- **연구 기준일**: 2026-10-06 (Asia/Seoul 기준 어제)
- **실제 검색 창**: 2026-10-06 단일일(0건) → 7일(2026-09-30~10-06, 0건) → **2026-09-07~2026-10-06 (30일)**
- **검색 질의**: `chest radiograph deep learning` (30일 창에서 보완 질의 `chest X-ray`도 사용)
- 30일 창에서도 목표 3편에 미달하여 **1편만 채택**함(관련성 기준은 낮추지 않음).

## 코호트 요약 (masked `llm.hospital` 뷰, 집계 값만)

- 흉부 단순촬영(CXR) 272건, 고유 환자 약 150명, 5개 기관
- 연령 9–87세, 성별 균형, PA 약 2/3 · AP 약 1/3
- 소견 라벨: 무소견 약 55%, 나머지는 Infiltration, Atelectasis, Nodule, Effusion 등 희소·다중 라벨
- 합성 데이터로 표시됨

## 채택 논문

### 1. CXR-LT 2026 challenge: Multi-center long-tailed and zero shot chest X-ray classification
- 링크: https://doi.org/10.1016/j.media.2026.104340 (Medical Image Analysis)
- **관련성**: 다기관 롱테일·zero-shot CXR 분류 챌린지 보고로, 여러 참가 방법을 공통 기준에서 비교한 결과라는 점에서 임상 적용성 판단에 도움이 됨.
- **우리 데이터가 뒷받침하는 점**: 우리 데이터는 5개 기관, 다중 라벨, 무소견 우세와 소수 희소 소견이라는 롱테일 분포를 보여 챌린지 설정과 유사함.
- **알 수 없는 점**: 출판처가 초록을 제공하지 않아(`abstract` 비움) 제목 외 세부 성능·방법은 확인하지 못함. 우리 코호트는 희소 소견별 표본이 매우 적어 롱테일 성능을 통계적으로 검증하기 어려움.

## 제외 사유 요약
기존 추천과 중복(Physician involvement, Learning to defer, ASH-MIL 등), CT·ECG·교육·서지 논문, ICU 사망 예측 CXR-EHR 모델(GLR-MM), 연합학습 프라이버시 방어(Aegis), 초록 없이 CXR 적용 여부를 확인할 수 없는 보고서 생성 논문은 제외함.

> 본 추천은 자동 검색 결과이며 반드시 의사의 검토가 필요합니다.
