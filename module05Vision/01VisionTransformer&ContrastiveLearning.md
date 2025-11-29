## 1. Vision Transformer

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

---

## 2. Contrastive Learning & CLIP

### 2.1 Contrastive Learning 기본 개념

#### 핵심 원리
- **유사도 학습**: 비슷한 것은 가까이, 다른 것은 멀리
- **자기지도학습**: 모델이 스스로 학습하여 라벨 없이 **Embedding Space** 생성

#### 주요 구성 요소
- **Cluster Prototypes**: 클러스터 중심점
- **Positive Pairs**: 유사한 샘플 쌍
- **Negative Pairs**: 다른 샘플 쌍

#### 유사도 측정
- **Cosine Similarity** 사용

### 2.2 Vision + LLM 통합: CLIP

CLIP (Contrastive Language-Image Pre-training)은 Vision과 Language를 결합한 모델

```
[이미지] ←→ Embedding Space ←→ [텍스트]
   ↓              ↓              ↓
Vision        Contrastive      Language
Encoder        Learning        Encoder
```

### 2.3 Contrastive Learning의 한계

#### 주요 문제점
1. **텍스트의 모호성**: 
   - 다의성(Ambiguity) 문제
   - 맥락에 따른 의미 변화

2. **추론 능력 부족**:
   - 단순 매칭을 넘어선 논리적 추론 제한

### 2.4 개선 방향 및 최신 기법

#### Multi-step Reasoning 도입
- **Chain of Thought**: 단계적 사고 과정 모델링
- **Chain of Tree/Forest**: 다중 경로 추론 구조

#### 데이터 증강 전략
- **합성 데이터(Synthetic Data)** 활용
- **시뮬레이션 데이터** 활용

---

## 핵심 요약

### Vision Transformer
- Global context 인식으로 CNN의 한계 극복
- Pre-training + Fine-tuning 전략
- 대규모 데이터와 높은 연산 비용 필요

### Contrastive Learning & CLIP
- Vision과 Language를 공통 임베딩 공간에서 학습
- 자기지도학습으로 라벨 없이 학습 가능
- Chain of Thought 등으로 추론 능력 개선 중

---

> **학습 포인트**: Vision AI는 CNN의 local feature 인식에서 Transformer의 global context 이해로 발전했으며, CLIP을 통해 언어와의 통합으로 더욱 강력한 이해 능력을 갖추게 되었습니다.
