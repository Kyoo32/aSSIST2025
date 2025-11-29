

## Lecture 9 Foundation Models

### 9.1 Segment Anything Model (SAM)

#### 구조
```
Image Encoder
    ↓
Prompt Encoder
    ↓
Mask Decoder
    ↓
Segmentation 결과
```

#### 특징
- **Foundation Model**: 범용적 세그멘테이션
- 다양한 객체와 상황에 적용 가능

### 9.2 Vision-Language Grounding

#### Grounding이란?
**언어 명령을 실제 이미지 내 객체와 연관짓는 기술**

#### 예시
```
텍스트: "빨간 모자를 쓴 사람"
    ↓
이미지에서 해당 객체 위치 특정
    ↓
Bounding Box 또는 Segmentation
```

---

## 핵심 요약

### Self-Supervised Learning
- MAE: 이미지 복원 학습
- V-JEPA: 미래 예측 학습 (World Model)

### 효율적인 Transformer
- Swin Transformer: 산업 실용화
- DeiT: 적은 데이터로 학습
- DINO: 완전 무라벨 학습

### Object Detection 진화
- R-CNN → YOLO → DETR → RT-DETR
- Segmentation, Depth, Tracking, Language와 결합

### 산업화 핵심
- 모델 경량화 (Pruning, Quantization, Distillation, NAS)
- Foundation Models (SAM, Grounding)

---

> **학습 포인트**: AI Vision은 단순 인식(Perception)에서 이해(Understanding)와 예측(Prediction)으로 진화했으며, Self-Supervised Learning과 경량화 기술을 통해 산업 현장에서 실용적으로 활용 가능한 수준에 도달했습니다.
