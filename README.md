## 강민성 (Minseong Kang)

**AI Researcher in Image-to-Video and Video Refinement**  
I2V/V2V 생성 영상 정제 · 동역학 보존 제약 · 생성 비디오 평가

---

### Research

현재 **Image-to-Video 생성 영상의 품질 향상 과정에서 기준 영상의 움직임 구조가 변형되는 문제**를 연구하고 있습니다.  
강한 Video-to-Video 정제 모델은 시각 품질을 높일 수 있지만, 기준 I2V 출력의 움직임 패턴을 함께 바꿀 수 있습니다. 저는 이 상충관계를 줄이기 위해 고정 I2V 백본 뒤에 학습 가능한 출력 정제 헤드인 **DyRefHead**를 결합하는 방법을 실험하고 있습니다.

**관심 연구 분야**

- Image-to-Video generation
- Video-to-Video refinement
- Motion and dynamics preservation
- Generative video evaluation
- Computer vision and deep learning

---

### Featured Research Project

#### [I2V-V2V Physics-Preserving Refinement](https://github.com/mints-s/I2V-V2V-Physics-Preserving-Refinement)

> I2V 생성 영상의 시각 품질을 개선하면서 기준 영상의 움직임 구조 이탈을 제한하기 위한 DyRefHead 출력 정제 연구

| 항목 | 내용 |
|------|------|
| 연구 주제 | 동역학 보존 제약 기반 I2V 출력 정제 |
| 기준 I2V 모델 | RealWonder |
| 정제 비교 모델 | VEnhancer n30 |
| 제안 구조 | DyRefHead v2 / v3 |
| 실험 장면 | 3 scenes |
| 영상 조건 | 256 x 256, 16 fps, 4 seconds |
| 평가 지표 | VBench Imaging, Motion Smoothness, mean Flow EPE, Flow magnitude ratio |

**핵심 아이디어**

- 기준 I2V 출력 `V0`를 실제 물리 정답이 아니라 동역학 선행정보로 정의
- VEnhancer n30 결과를 시각 품질 의사 목표로 사용
- DyRefHead가 직접 영상을 대체하지 않고 residual refinement를 예측
- 시간 변화량 보존과 첫 프레임 정체성 제약으로 움직임 이탈을 제한
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

본 연구는 3개 장면 기반의 초기 검증입니다. Flow 기반 지표는 실제 물리 정합성의 증명이 아니라 기준 I2V 출력 대비 움직임 이탈 정도를 측정하는 보조 지표로 사용했습니다.

---

### Contact

- Email: kingsman518@gmail.com
- GitHub: [github.com/mints-s](https://github.com/mints-s)

---

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=mints-s&layout=compact&langs_count=8&hide=html,css)

[![GitHub Streak](https://streak-stats.demolab.com?user=mints-s&theme=default)](https://git.io/streak-stats)
