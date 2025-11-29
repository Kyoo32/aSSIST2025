## Lecture 8 Object Detection의 확장

### 8.1 Segmentation과의 결합

#### 진화 방향
```
객체 중심 → 픽셀 단위 의미 이해
```

#### 세분화 수준
1. **Instance Segmentation**: 개별 객체 구분
2. **Semantic Segmentation**: 의미적 영역 구분

### 8.2 Depth와의 결합

#### 목적
- **"어디에 있는가"를 3차원으로 이해**

#### Uncertainty Estimation
- 불확실성까지 예측
- **활용**: 위험 회피, 안전성 향상

### 8.3 Object Tracking (MOT - Multiple Object Tracking)

```
Detection + Tracking = 시간 축 속 객체 인식 지속
```

#### 의의
- 단일 프레임 인식 → 연속적인 추적

### 8.4 Vision-Language 결합

#### Open-Vocabulary Detection
```
텍스트 + 이미지 공동 임베딩
    ↓
기존 탐지 한계 극복
    ↓
새로운 클래스도 탐지 가능
```
