# 2026-09-23 논문 추천

- **연구 기준일**: 2026-09-23 (Asia/Seoul 기준 어제)
- **실제 검색 창**: 2026-09-23 단일일(0건) → 2026-09-17~2026-09-23 (7일, 신규 논문 없음, 기존 추천과 중복) →
  **2026-08-25~2026-09-23 (30일)** 에서 신규·적합 논문 3편을 확보하여 채택.
  (MICCAI/IPMI/CVPR/NeurIPS/ICLR arXiv 소스는 이번 검색에서 모두 HTTP 406으로 응답 없음, OpenAlex 저널만 반환됨)
- **검색 질의**: `chest radiograph deep learning multicenter` (1차), 보조 질의로
  `chest X-ray thoracic disease classification`, `pulmonary nodule AI reader study CT` 사용

## 코호트 요약 (masked `llm.hospital` 뷰, 환자 단위 값 없음)

- 총 272건의 흉부 단순촬영(CXR) 레코드, 고유 환자 153명, 5개 기관(INST01–05, 기관당 48–62건) 분포
- 성별 균형 (남 136 / 여 136), 연령 9–87세, 평균 51.5세
- 촬영 자세: PA 184건, AP 88건
- 소견 라벨: 무소견(No Finding) 145건이 최다, 이어서 Infiltration(21), Atelectasis(16), Nodule(7),
  Fibrosis/Effusion(각 6), Cardiomegaly(5), Pneumothorax(5) 등 다중 라벨 조합 다수 존재
- 전 레코드가 `is_synthetic = true`로 표시된 합성/시뮬레이션 데이터셋임

이 코호트는 다기관·다양한 연령대의 흉부 영상 판독 데이터이며, 폐결절/침윤/무기폐 등
일반적인 흉부 소견과 저선량·합성 영상 이슈에 대한 임상적 관심사와 맞닿아 있음.

## 채택 논문

### 1. Staged purpose-blinded evaluation of provenance risk from a general-purpose generator in breast ultrasound
- **관련성**: 범용 생성형 AI가 만든 의료 영상이 임상의를 속일 수 있는지를 정량 평가한 리더 스터디로,
  우리 데이터셋이 전량 `is_synthetic = true`인 합성 영상 코호트라는 점과 직접 맞닿아 있음 — 합성 영상의
  신뢰성·출처(provenance) 검증 문제는 우리 데이터의 해석에도 그대로 적용됨.
- **우리 데이터가 뒷받침하는 점**: 전체 레코드가 합성 데이터로 표시되어 있어, 판독자가 합성 여부를
  명시적으로 인지하지 못하면 실제 소견처럼 오인할 위험이 존재함을 보여주는 근거가 됨.
- **알 수 없는 점**: 유방 초음파 대상 연구이므로 흉부 X-ray에 대한 판독자 인지율은 직접 검증되지 않음.

### 2. Benchmarking AI-generated thin-slice CT under clinical reconstruction conditions: a multicohort study
- **관련성**: 다기관 코호트에서 AI 생성 영상(합성 박편 CT)의 임상 활용 가능성과 한계를 리더 스터디로
  검증하여, 합성 영상의 신뢰도와 임상 적용 범위를 어떻게 검증해야 하는지 구조를 제시함.
- **우리 데이터가 뒷받침하는 점**: 다기관(5개 기관) 코호트 구조가 유사하며, AI 생성 영상의 외부 검증
  필요성이라는 주제가 우리의 합성 CXR 데이터셋 해석에도 적용 가능함.
- **알 수 없는 점**: CT 영상 대상 연구로, 흉부 단순촬영(CXR)에 대한 결과로 일반화할 수 있는지는 불확실함.

### 3. Quantitative and qualitative lung parameters in photon-counting CT: comparison of ultra-low-dose with standard low-dose protocols
- **관련성**: 저선량 촬영이 폐 실질/기도 소견의 정량·정성 평가에 미치는 영향을 전향적으로 검증한
  임상 연구로, 영상 획득 조건이 판독 결과에 미치는 영향을 이해하는 데 유용함.
- **우리 데이터가 뒷받침하는 점**: 우리 코호트에도 다양한 영상 품질/기관별 장비 차이가 존재할 수 있어,
  저선량·영상 조건에 따른 소견 편향 가능성을 고려할 근거가 됨.
- **알 수 없는 점**: CT 기반 연구이며 PA/AP 단순촬영에는 직접 해당하지 않아, 결론을 CXR 판독에 그대로
  적용할 수는 없음.

## 공통 축

- **합성 영상 신뢰성**: 합성/생성 영상이 판독자를 속이거나 임상 결정에 영향을 줄 수 있는지
- **판독자 영향/워크플로**: AI 보조 도구나 합성 영상이 판독자의 시간, 신뢰도, 의사결정에 미치는 영향
- **영상 품질·저선량 영향**: 촬영 조건(선량, 기관, 장비)이 소견 검출과 정량 지표에 미치는 영향

## 참고 링크

- https://doi.org/10.1038/s41746-026-03209-w
- https://doi.org/10.1038/s41746-026-03253-6
- https://doi.org/10.1007/s00330-026-12887-9

**주의**: 위 추천은 자동 검색 및 코호트 통계에 기반한 참고 자료이며, 임상 적용 전 반드시
담당 의료진의 검토와 판단이 필요합니다.
