## Lecture 6: Object Detection의 진화

### 6.1 Object Detection 발전사

#### R-CNN (2014)
```
Region Proposal → Feature Extraction → Classification
```
- "어디에 물체가 있는 것 같은가?"를 찾음

#### YOLO (You Only Look Once)
- **실시간 객체 탐지의 시작**
- 현재도 산업 현장에서 많이 사용

#### DETR (Detection Transformer)
- **Transformer 기반**
- 맥락 인식 가능 → **물체가 겹쳐도 인식 가능**

#### RT-DETR (Real-Time DETR)
- **실시간 성능 달성**: >30 FPS

#### Deformable DETR
- **Sparse Attention 기반**
- 전역 Attention의 한계 극복

### 6.2 Object Detection 성능 평가 지표

#### 주요 지표
1. **Precision & Recall**
   - Precision: 예측한 것 중 정답 비율
   - Recall: 정답 중 찾은 비율

2. **IoU (Intersection over Union)**
   - 예측 박스와 실제 박스의 겹침 정도

3. **mAP (mean Average Precision)**
   - 보통 IoU 0.5 기준 사용
