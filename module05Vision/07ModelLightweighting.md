## Lecture 7 산업 활용을 위한 모델 경량화

### 7.1 경량화 기법

**핵심**: 데이터 & 모델 & 학습의 균형 맞추기

#### 1. Model Pruning (가지치기)
```
불필요한 Neuron 삭제 → 모델 크기 감소
```

#### 2. Quantization (양자화)
- 모델 파라미터의 정밀도 감소
- **주의**: 일부 성능 손실 발생 가능

#### 3. Knowledge Distillation (지식 증류)
```
큰 모델(Teacher) → 작은 모델(Student)로 지식 전달
```

#### 4. Neural Architecture Search (NAS)
- 경사하강법 등을 활용한 **최적 구조 자동 탐색**

### 7.2 AI Vision Pipeline 구조

```
Input Layer
    ↓
Detection Layer (객체 탐지)
    ↓
Analysis Layer (분석)
    ↓
Control Layer (제어/의사결정)
```
