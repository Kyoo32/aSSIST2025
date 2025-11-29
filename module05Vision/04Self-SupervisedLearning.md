## Lecture 4 Self-Supervised Learning

### 4.1 Masked AutoEncoder (MAE)

#### 작동 원리
```
입력 이미지
    ↓
일부 패치 마스킹 (Masking)
    ↓
Encoder: Feature 추출
    ↓
Decoder: 마스킹된 패치 복원
    ↓
원본 이미지 재구성
```

#### 핵심 개념
- 라벨 없이 이미지 자체로부터 학습
- 가려진 부분을 예측하며 표현 학습

### 4.2 V-JEPA (Vision Joint Embedding Predictive Architecture)

#### MAE와의 차이점
- **입력**: 단일 이미지 → **시간 연속 프레임**
- **목표**: 이미지 복원 → **미래 상태 예측**

#### 작동 과정
```
연속 프레임 입력
    ↓
일부 프레임 마스킹
    ↓
모델이 미래 상태 예측
    ↓
World Model 구축
```

#### 의의
- **World Model** 개념의 시작
- 단순 인식을 넘어 예측 능력 확보
