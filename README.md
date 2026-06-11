강민성 (Minseong Kang)

Computer Vision Researcher
Generative Video · Motion & Dynamics Preservation · Video Quality Evaluation

---

About

컴퓨터 비전과 딥러닝을 기반으로 영상의 생성과 정제 문제를 연구합니다.
특히 생성된 영상에서 시각 품질과 움직임 구조를 동시에 만족시키는 방법에 관심이 있습니다.

현재는 Image-to-Video(I2V) / Video-to-Video(V2V) 파이프라인에서, 강한 정제가 시각 품질을 높이는 동시에 기준 영상의 움직임 구조를 바꿔버리는 상충관계를 정량적으로 분석하고 완화하는 연구를 진행하고 있습니다.

---

Research Interests

Core


Computer Vision & Deep Learning
Video understanding and generation


Generative Video — current focus


Image-to-Video / Video-to-Video generation & refinement
Motion and dynamics preservation
Generative video evaluation (visual quality vs. motion fidelity)


Methodology


Optical-flow based auxiliary metrics for motion deviation
Residual refinement & constraint-based learning

---

Featured Project

I2V-V2V Physics-Preserving Refinement


I2V 생성 영상의 시각 품질을 개선하면서 기준 영상의 움직임 구조 이탈을 제한하기 위한 DyRefHead 출력 정제 연구

---

고정된 I2V 백본이 생성한 기준 영상의 움직임 구조를 동역학 선행정보(dynamics prior) 로 보고, 그 후단에 학습 가능한 출력 정제 헤드 DyRefHead를 결합해 시각 품질 개선 과 움직임 보존 사이의 상충관계를 분석합니다.

항목내용연구 주제동역학 보존 제약 기반 I2V 출력 정제기준 I2V 모델RealWonder정제 비교 모델VEnhancer n30제안 구조DyRefHead v2 / v3실험 장면3 scenes영상 조건256 × 256, 16 fps, 4 seconds평가 지표VBench Imaging · Motion Smoothness · mean Flow EPE · Flow magnitude ratio코드 구성Python 90.4% · Shell 9.6%

핵심 아이디어


기준 I2V 출력 V0를 실제 물리 정답이 아니라 동역학 선행정보로 정의
VEnhancer n30 결과를 시각 품질 의사 목표(pseudo target)로 사용
DyRefHead가 영상을 직접 대체하지 않고 residual refinement 를 예측 → V_hat = clip(V0 + α·R_θ(V0), 0, 1)
시간 변화량 보존(L_temp)과 첫 프레임 정체성 제약(L_id)으로 움직임 이탈을 제한
시각 품질 개선과 동역학 보존 사이의 trade-off를 정량 분석


text[Input Image / Action Condition]
        |
[Frozen I2V Backbone: RealWonder]
        |
[Stage-1 Video V0]
        |
[DyRefHead: Residual Output Refinement]
        |
[Refined Video V_hat]
        |
[Evaluation: VBench + Flow-based Auxiliary Metrics]

대표 결과

MethodVBench Imaging ↑mean Flow EPE ↓Flow Ratio ≈ 1Stage-1 I2V output0.61870.00001.0000VEnhancer n300.65870.27823.4906DyRefHead v20.62420.18831.6971DyRefHead v30.62220.19011.5899

DyRefHead v2는 VEnhancer n30만큼 강한 시각 정제를 달성하지는 못했지만, 기준 I2V 출력보다 VBench Imaging을 소폭 향상시키면서 VEnhancer보다 낮은 움직임 이탈 보조 지표를 보였습니다.


Currently / Next


장면 수 확장 및 더 강한 물리 기반 벤치마크 적용
user preference 기반 정성 평가 추가
residual refinement 구조와 동역학 제약의 일반화 가능성 검증

---

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=mints-s&layout=compact&langs_count=8&hide=html,css)

[![GitHub Streak](https://streak-stats.demolab.com?user=mints-s&theme=default)](https://git.io/streak-stats)
