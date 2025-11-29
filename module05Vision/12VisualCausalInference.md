## Lecture 12 Visual Causal Inference

### 12.1 인과 추론의 핵심 질문

**"무엇이 무엇을 변화시키는가?"**

#### 상관관계에서 인과관계로
```
Correlation (상관관계)
"A와 B가 함께 나타난다"
    ↓
Causal Graph (인과 그래프)
"A가 B를 일으킨다"
    ↓
Intervention (개입)
"A를 바꾸면 B가 어떻게 변할까?"
```

### 12.2 인과 추론의 단계

#### 1. Correlation (상관관계 발견)
```python
# 예시: 우산 사용과 비 사이의 관계 관찰
우산 사용 ↔ 비
```

#### 2. Causal Graph (인과 그래프 구성)
```
비 → 우산 사용
(비가 우산 사용을 야기함)
```

#### 3. Intervention (개입 실험)
```
"우산을 강제로 사용하게 하면?"
→ 비가 오지 않음 (인과관계 확인)
```

### 12.3 Visual Causal Inference의 의의

#### AGI를 향한 핵심 능력
- **예측을 넘어선 이해**: "왜?"에 답할 수 있음
- **반사실적 추론(Counterfactual Reasoning)**: "만약 ~했다면?"
- **능동적 개입**: 원인을 조작하여 결과 제어

