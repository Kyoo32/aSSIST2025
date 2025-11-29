## Lecture 13 World Model - 미래를 예측하는 AI

### 13.1 World Model의 개념

#### 정의
**환경을 내부적으로 시뮬레이션하여 미래를 예측하는 모델**

#### 3대 핵심 기능
```
1. 관측 압축 (Observation Compression)
   현실 세계의 복잡한 정보를 효율적으로 표현

2. 미래 예측 (Future Prediction)
   다음 상태가 어떻게 될지 예측

3. 행동 결정 (Action Decision)
   최적의 행동 선택
```

### 13.2 World Model의 작동 구조

```
환경 관찰
    ↓
상태 압축 (Latent Representation)
    ↓
미래 상태 예측
    ↓
행동 계획
    ↓
실제 행동 수행
    ↓
결과 관찰 (피드백)
```

### 13.3 주요 World Model 연구

#### 1. Google PlaNet (2019)
- **Deep Planning Network**
- 모델 기반 강화학습
- 시각 입력으로부터 미래 계획

#### 2. DeepMind Dreamer (2020)
- **Dreamer v1, v2, v3**
- 잠재 공간(Latent Space)에서 꿈꾸듯 미래 시뮬레이션
- 실제 경험 없이 상상으로 학습

#### 3. Meta Genie (2024)
- **Foundation World Model**
- 게임 환경 등에서 일반화된 World Model
- 인터랙티브 환경 생성 가능

### 13.4 World Model의 응용

```
자율주행
- 다음 상황 예측
- 안전한 경로 계획

로봇 제어
- 행동 결과 시뮬레이션
- 최적 동작 선택

게임 AI
- 상대방 행동 예측
- 전략 수립
```
