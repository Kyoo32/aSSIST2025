NumPy는 데이터 사이언스의 핵심 라이브러리입니다. "Numerical Python"의 줄임말로, 다차원 배열과 수치 연산을 효율적으로 처리할 수 있게 해줍니다. Numpy는 Pandas의 백엔드 라이브러리로도 사용됩니다. 

## NumPy 설치 및 임포트

```python
# 설치 (터미널에서)
# pip install numpy

# 임포트
import numpy as np
```

## 1. NumPy 배열 생성

### 리스트에서 배열 생성

```python
import numpy as np

# 1차원 배열
arr1 = np.array([1, 2, 3, 4, 5])
print(arr1)  # [1 2 3 4 5]
print(type(arr1))  # <class 'numpy.ndarray'>

# 2차원 배열
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
print(arr2)
# [[1 2 3]
#  [4 5 6]]
```

### 다양한 배열 생성 함수

```python
# 영배열 (0으로 채워진 배열)
zeros = np.zeros(5)
print(zeros)  # [0. 0. 0. 0. 0.]

zeros_2d = np.zeros((3, 4))  # 3x4 영배열
print(zeros_2d)

# 일배열 (1로 채워진 배열)
ones = np.ones(5)
print(ones)  # [1. 1. 1. 1. 1.]

# 연속된 숫자 배열
range_arr = np.arange(0, 10, 2)  # 0부터 10까지 2씩 증가
print(range_arr)  # [0 2 4 6 8]

# 균등하게 나눈 배열
linspace_arr = np.linspace(0, 1, 5)  # 0과 1 사이를 5개로 균등분할
print(linspace_arr)  # [0.   0.25 0.5  0.75 1.  ]

# 랜덤 배열
random_arr = np.random.choice(range(100), size=4)  # 0~100 사이 랜덤 값 4개
print(random_arr)
```

## 2. 배열의 속성

```python
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])

print(f"배열: \n{arr}")
print(f"차원: {arr.ndim}")      # 2 (2차원)
print(f"형태: {arr.shape}")     # (3, 4) - 3행 4열
print(f"크기: {arr.size}")      # 12 (전체 원소 개수)
print(f"데이터 타입: {arr.dtype}")  # int64
```

## 3. 배열 인덱싱과 슬라이싱

```python
arr = np.array([10, 20, 30, 40, 50])

# 인덱싱
print(arr[0])   # 10 (첫 번째 원소)
print(arr[-1])  # 50 (마지막 원소)

# 슬라이싱
print(arr[1:4])   # [20 30 40]
print(arr[:3])    # [10 20 30]
print(arr[2:])    # [30 40 50]

# 2차원 배열
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

print(arr_2d[0, 1])    # 2 (첫 번째 행, 두 번째 열)
print(arr_2d[1])       # [4 5 6] (두 번째 행 전체)
print(arr_2d[:, 0])    # [1 4 7] (첫 번째 열 전체)
print(arr_2d[0:2, 1:3]) # [[2 3] [5 6]] (부분 배열)
```

## 4. 수학 연산

### 기본 산술 연산

```python
arr1 = np.array([1, 2, 3, 4])
arr2 = np.array([10, 20, 30, 40])

# 원소별 연산
print(arr1 + arr2)  # [11 22 33 44]
print(arr1 - arr2)  # [-9 -18 -27 -36]
print(arr1 * arr2)  # [10 40 90 160]
print(arr1 / arr2)  # [0.1 0.1 0.1 0.1]

# 스칼라와의 연산
print(arr1 * 2)     # [2 4 6 8]
print(arr1 + 5)     # [6 7 8 9]
```

### 통계 함수

```python
data = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

print(f"합계: {np.sum(data)}")        # 55
print(f"합계: {data.sum()}")          # 55

print(f"평균: {np.mean(data)}")       # 5.5
print(f"평균: {data.mean()}")         # 5.5

print(f"중간값: {np.median(data)}")   # 5.5
print(f"표준편차: {np.std(data)}")    # 2.8722813232690143
print(f"최댓값: {np.max(data)}")      # 10
print(f"최솟값: {np.min(data)}")      # 1
print(f"최댓값 인덱스: {np.argmax(data)}")  # 9
print(f"최솟값 인덱스: {np.argmin(data)}")  # 0
```

## 5. 데이터 분석 실용 예제

### 학생 성적 분석

```python
# 5명 학생의 3과목 성적 (행: 학생, 열: 과목)
scores = np.array([
    [85, 90, 78],  # 학생1: 수학, 영어, 과학
    [92, 88, 84],  # 학생2
    [78, 85, 90],  # 학생3
    [88, 92, 86],  # 학생4
    [90, 87, 92]   # 학생5
])

print("=== 학생별 성적 분석 ===")
# 각 학생의 평균 점수
student_averages = np.mean(scores, axis=1)  # axis=1: 행 방향으로 평균
for i, avg in enumerate(student_averages):
    print(f"학생 {i+1} 평균: {avg:.1f}점")

print("\n=== 과목별 성적 분석 ===")
# 각 과목의 평균 점수
subject_averages = np.mean(scores, axis=0)  # axis=0: 열 방향으로 평균
subjects = ['수학', '영어', '과학']
for subject, avg in zip(subjects, subject_averages):
    print(f"{subject} 평균: {avg:.1f}점")

print(f"\n전체 평균: {np.mean(scores):.1f}점")
print(f"최고 점수: {np.max(scores)}점")
print(f"최저 점수: {np.min(scores)}점")
```

### 판매 데이터 분석

```python
# 12개월 월별 판매량
monthly_sales = np.array([150, 200, 180, 220, 250, 300, 280, 320, 290, 260, 240, 200])
months = np.array(['1월', '2월', '3월', '4월', '5월', '6월', 
                   '7월', '8월', '9월', '10월', '11월', '12월'])

print("=== 판매 데이터 분석 ===")
print(f"연간 총 판매량: {np.sum(monthly_sales)}개")
print(f"월 평균 판매량: {np.mean(monthly_sales):.1f}개")
print(f"판매량 표준편차: {np.std(monthly_sales):.1f}")

# 최고/최저 판매 월
max_month_idx = np.argmax(monthly_sales)
min_month_idx = np.argmin(monthly_sales)

print(f"최고 판매 월: {months[max_month_idx]} ({monthly_sales[max_month_idx]}개)")
print(f"최저 판매 월: {months[min_month_idx]} ({monthly_sales[min_month_idx]}개)")

# 분기별 분석 (3개월씩 묶어서)
quarterly_sales = monthly_sales.reshape(4, 3)  # 4분기 x 3개월로 변형
quarterly_totals = np.sum(quarterly_sales, axis=1)

for i, total in enumerate(quarterly_totals):
    print(f"{i+1}분기 총 판매량: {total}개")
```

## 6. 배열 조건 필터링

```python
data = np.array([85, 92, 78, 88, 90, 76, 94, 82])

# 조건에 맞는 데이터 찾기
high_scores = data[data >= 90]  # 90점 이상
print(f"90점 이상: {high_scores}")  # [92 90 94]

low_scores = data[data < 80]    # 80점 미만
print(f"80점 미만: {low_scores}")   # [78 76]

# 복합 조건
middle_scores = data[(data >= 80) & (data < 90)]
print(f"80점 이상 90점 미만: {middle_scores}")  # [85 88 82]
```

## 7. 유용한 함수들

```python
# 배열 정렬
arr = np.array([64, 34, 25, 12, 22, 11, 90])
print(f"원본: {arr}")
print(f"정렬: {np.sort(arr)}")          # 오름차순
print(f"역순 정렬: {np.sort(arr)[::-1]}")  # 내림차순

# 고유값 찾기
data = np.array([1, 2, 2, 3, 3, 3, 4, 4, 5])
unique_values = np.unique(data)
print(f"고유값: {unique_values}")  # [1 2 3 4 5]

# 배열 합치기
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
combined = np.concatenate([arr1, arr2])
print(f"합친 배열: {combined}")  # [1 2 3 4 5 6]
```

## 실습 과제

다음 코드를 실행해보고 결과를 분석해보세요:

```python
# 가상의 주식 가격 데이터
stock_prices = np.array([100, 102, 98, 105, 108, 103, 110, 107, 112, 115])

# 1. 기본 통계 계산
print("=== 주식 가격 분석 ===")
print(f"평균 주가: ${np.mean(stock_prices):.2f}")
print(f"최고가: ${np.max(stock_prices)}")
print(f"최저가: ${np.min(stock_prices)}")

# 2. 일일 변화율 계산
daily_changes = np.diff(stock_prices)  # 연속된 값들의 차이
print(f"일일 변화: {daily_changes}")

# 3. 상승일과 하락일 분석
up_days = np.sum(daily_changes > 0)
down_days = np.sum(daily_changes < 0)
print(f"상승일: {up_days}일, 하락일: {down_days}일")
```

NumPy는 데이터 사이언스의 기초가 되는 라이브러리입니다. 이후 배울 Pandas, Matplotlib 등도 모두 NumPy를 기반으로 동작합니다!
