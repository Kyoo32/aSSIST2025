

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
