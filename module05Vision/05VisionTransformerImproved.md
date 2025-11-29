
## Lecture 5 효율적인 Vision Transformer 변형

### 5.1 Swin Transformer: 계층적 비전 표현

#### 개발 배경
- ViT가 무겁고 비용이 높음
- CNN의 아이디어 차용

#### 핵심 혁신
**Global Attention → Shifted Windows**

#### 장점
- 시간 효율성 대폭 향상
- **산업 현장에서 실용적으로 사용 가능한 수준** 달성

### 5.2 DeiT: Data-Efficient Transformer

#### 구조: Teacher-Student 학습

```
Teacher 모델 (대규모 사전 학습)
    ↓
  지식 전달
    ↓
Student 모델 (필요한 것만 학습)
```

#### Distillation Token
- Teacher의 예측 확률을 Student가 학습
- 모델 경량화 + 성능 보장
- **적은 데이터 상황에서도 효과적**

### 5.3 DINO: Self-Distillation

#### 독특한 구조
- **하나의 모델이 Teacher와 Student 역할 동시 수행**

#### 학습 메커니즘
```
Student 모델
    ↓
예측 생성
    ↓
Teacher 모델 (EMA 업데이트로 안정적 유지)
    ↓
Self-Distillation: Teacher 확률 분포를 Student가 모방
```

#### 특징
- **완전한 무라벨 학습(Unsupervised)**
- Teacher가 Student보다 안정적으로 유지됨
