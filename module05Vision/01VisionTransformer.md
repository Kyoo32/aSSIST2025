## Lecture1 Vision Transformer

### 1.1 Vision AI의 발전 과정
- **핵심 목표**: Seeing → Understanding
- **기술 발전 단계**:
  - RuleBased → DataDriven → Deep Learning → AttentionDriven

### 1.2 CNN에서 Transformer로의 전환
**발전 경로**: CNN → Transformer → VLM (Vision Language Model)

#### CNN의 특징과 한계
- **장점**: Local feature 인식 가능
- **한계**: 추상적인 분류는 가능하나 세부 분류는 어려움
  - 예시: "강아지"는 인식하지만 "강아지 품종" 구분은 어려움

#### Vision Transformer의 강점
- **Global Context 인식**: 전체적인 맥락을 하나로 인식
- **핵심 메커니즘**: Attention + Residual Connection
  - Long-term dependency 문제 해결
  - 정보의 흐름이 끊기지 않도록 유지

### 1.3 Vision Transformer 기본 구조

```
이미지 입력
    ↓
패치 분할 (Patch)
    ↓
패치 임베딩 (Patch Embedding)
    ↓
위치 임베딩 (Positional Embedding)
    ↓
Class Token 추가
    ↓
Transformer Encoder (Pre-Norm 구조)
    ↓
출력
```

#### 구조적 특징
- **이미지 처리 과정**:
  1. 이미지를 패치(Patch)로 분할
  2. 각 패치를 임베딩으로 변환
  3. 위치 정보 추가 (Positional Embedding)
  4. Class Token 추가
  
- **NLP와의 차이점**: 
  - Pre-Norm 구조 사용 (Normalization을 사전에 적용)

### 1.4 학습 과정

#### 2단계 학습 전략
1. **Pre-training**: 대규모 데이터셋으로 사전 학습
2. **Fine-tuning**: 소규모 데이터셋으로 미세 조정

#### 학습 방법론
- Transfer Learning (전이 학습)
- Zero-shot Learning (제로샷 학습)

### 1.5 Vision Transformer의 한계

- **데이터 요구사항**: 대규모 데이터셋 필요
- **연산 비용**: 높은 컴퓨팅 리소스 요구
