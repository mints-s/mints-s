# 강민성 (Minseong Kang)

**Computer Vision Researcher**
Generative Video · Motion & Dynamics Preservation · Video Quality Evaluation

---

### About

컴퓨터 비전과 딥러닝을 기반으로 **영상의 생성과 정제** 문제를 연구합니다.
특히 생성된 영상에서 **시각 품질과 움직임 구조를 동시에 만족**시키는 방법에 관심이 있습니다.

현재는 Image-to-Video(I2V) / Video-to-Video(V2V) 파이프라인에서, 강한 정제가 시각 품질을 높이는 동시에 기준 영상의 움직임 구조를 바꿔버리는 **상충관계를 정량적으로 분석하고 완화**하는 연구를 진행하고 있습니다.

연구뿐 아니라 Java / Spring Boot 기반 백엔드 개발 경험이 있어, 실험 파이프라인과 평가 자동화를 직접 구축하고 운영하는 것을 선호합니다.

---

### Research Interests

**Core**

- Computer Vision & Deep Learning
- Video understanding and generation

**Generative Video — *current focus***

- Image-to-Video / Video-to-Video generation & refinement
- Motion and dynamics preservation
- Generative video evaluation (visual quality vs. motion fidelity)

**Methodology**

- Optical-flow based auxiliary metrics for motion deviation
- Residual refinement & constraint-based learning

---

### Featured Project

#### [I2V-V2V Physics-Preserving Refinement](https://github.com/mints-s/I2V-V2V-Physics-Preserving-Refinement)

> I2V 생성 영상의 시각 품질을 개선하면서 기준 영상의 움직임 구조 이탈을 제한하기 위한 DyRefHead 출력 정제 연구

고정된 I2V 백본이 생성한 기준 영상의 움직임 구조를 **동역학 선행정보(dynamics prior)** 로 보고, 그 후단에 학습 가능한 출력 정제 헤드 **DyRefHead**를 결합해 *시각 품질 개선* 과 *움직임 보존* 사이의 상충관계를 분석합니다.

| 항목 | 내용 |
|------|------|
| 연구 주제 | 동역학 보존 제약 기반 I2V 출력 정제 |
| 기준 I2V 모델 | RealWonder |
| 정제 비교 모델 | VEnhancer n30 |
| 제안 구조 | DyRefHead v2 / v3 |
| 실험 장면 | 3 scenes |
| 영상 조건 | 256 × 256, 16 fps, 4 seconds |
| 평가 지표 | VBench Imaging · Motion Smoothness · mean Flow EPE · Flow magnitude ratio |
| 코드 구성 | Python 90.4% · Shell 9.6% |

**핵심 아이디어**

- 기준 I2V 출력 `V0`를 실제 물리 정답이 아니라 동역학 선행정보로 정의
- VEnhancer n30 결과를 시각 품질 의사 목표(pseudo target)로 사용
- DyRefHead가 영상을 직접 대체하지 않고 **residual refinement** 를 예측 → `V_hat = clip(V0 + α·R_θ(V0), 0, 1)`
- 시간 변화량 보존(`L_temp`)과 첫 프레임 정체성 제약(`L_id`)으로 움직임 이탈을 제한
- 시각 품질 개선과 동역학 보존 사이의 trade-off를 정량 분석

```text
[Input Image / Action Condition]
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
```

**대표 결과**

| Method | VBench Imaging ↑ | mean Flow EPE ↓ | Flow Ratio ≈ 1 |
|---|---:|---:|---:|
| Stage-1 I2V output | 0.6187 | 0.0000 | 1.0000 |
| VEnhancer n30 | 0.6587 | 0.2782 | 3.4906 |
| DyRefHead v2 | 0.6242 | 0.1883 | 1.6971 |
| DyRefHead v3 | 0.6222 | 0.1901 | 1.5899 |

DyRefHead v2는 VEnhancer n30만큼 강한 시각 정제를 달성하지는 못했지만, 기준 I2V 출력보다 VBench Imaging을 소폭 향상시키면서 VEnhancer보다 낮은 움직임 이탈 보조 지표를 보였습니다.

---

### Currently / Next

- 장면 수 확장 및 더 강한 물리 기반 벤치마크 적용
- user preference 기반 정성 평가 추가
- residual refinement 구조와 동역학 제약의 일반화 가능성 검증

---

### Tech Stack

**AI / ML**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)

**Computer Vision / Video**
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white)
![FFmpeg](https://img.shields.io/badge/FFmpeg-007808?style=flat&logo=ffmpeg&logoColor=white)
![imageio](https://img.shields.io/badge/imageio-4B8BBE?style=flat&logoColor=white)
![scikit-image](https://img.shields.io/badge/scikit--image-F7931E?style=flat&logoColor=white)

**Backend / Tools**
![Java](https://img.shields.io/badge/Java-007396?style=flat&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat&logo=springboot&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)

---

### Research Note

| 상태 | 제목 |
|------|------|
| 작성 완료 | Image-to-Video 생성 영상의 품질 향상을 위한 동역학 보존 제약 기반 출력 정제 헤드에 관한 연구 |

위 연구는 3개 장면 기반의 초기 검증입니다. Flow 기반 지표는 실제 물리 정합성의 증명이 아니라, 기준 I2V 출력 대비 움직임 이탈 정도를 측정하는 보조 지표로 사용했습니다.

---

<!-- 필요하면 아래에 연락처/링크를 추가하세요 (이메일, LinkedIn, 블로그 등) -->
