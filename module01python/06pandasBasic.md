
# Python 라이브러리 for Data Science - Pandas

Pandas는 데이터 분석과 조작을 위한 가장 중요한 Python 라이브러리입니다. "Panel Data"에서 유래된 이름으로, 구조화된 데이터를 쉽게 다룰 수 있게 해줍니다.

## Pandas 설치 및 임포트

```python
# 설치 (터미널에서)
# pip install pandas

# 임포트
import pandas as pd
import numpy as np
```

## 1. Pandas의 주요 특성

### Pandas의 핵심 장점

- **구조화된 데이터 처리**: 테이블 형태의 데이터를 Excel처럼 쉽게 다룰 수 있음
- **다양한 파일 형식 지원**: CSV, Excel, JSON, SQL 등 다양한 형식의 데이터 읽기/쓰기
- **강력한 데이터 조작**: 필터링, 정렬, 그룹핑, 병합 등의 기능
- **결측치 처리**: 누락된 데이터를 효과적으로 처리
- **시계열 데이터 분석**: 날짜/시간 데이터 처리에 특화

### 주요 데이터 구조

- **Series**: 1차원 데이터 (인덱스가 있는 배열)
- **DataFrame**: 2차원 데이터 (행과 열이 있는 테이블)

## 2. DataFrame 개념 이해

DataFrame은 Pandas의 핵심 데이터 구조로, 행(row)과 열(column)로 구성된 2차원 테이블입니다.

### DataFrame 생성

```python
import pandas as pd

# 딕셔너리로 DataFrame 생성
data = {
    '이름': ['김철수', '이영희', '박민수', '최지현', '정다은'],
    '나이': [25, 30, 35, 28, 32],
    '직업': ['개발자', '디자이너', '기획자', '마케터', '분석가'],
    '연봉': [4500, 4000, 5000, 3800, 4200]
}

df = pd.DataFrame(data)
print(df)
```

**출력:**

```
    이름  나이     직업    연봉
0  김철수  25    개발자  4500
1  이영희  30   디자이너  4000
2  박민수  35    기획자  5000
3  최지현  28    마케터  3800
4  정다은  32    분석가  4200
```

### DataFrame 기본 정보 확인

```python
# DataFrame 기본 정보
print("=== DataFrame 기본 정보 ===")
print(f"형태(shape): {df.shape}")           # (5, 4) - 5행 4열
print(f"크기(size): {df.size}")             # 20
print(f"컬럼명: {list(df.columns)}")         # ['이름', '나이', '직업', '연봉']
print(f"인덱스: {list(df.index)}")           # [0, 1, 2, 3, 4]

# 데이터 타입 확인
print("\n=== 데이터 타입 ===")
print(df.dtypes)

# 간단한 통계 정보
print("\n=== 수치형 컬럼 통계 ===")
print(df.describe())
```

## 3. 데이터 불러오기

### CSV 파일 읽기

```python
# CSV 파일 생성 (실습용)
sample_data = {
    'ID': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    '이름': ['김철수', '이영희', '박민수', '최지현', '정다은', 
           '황태권', '강미래', '서진우', '윤소라', '조한별'],
    '부서': ['IT', 'HR', 'IT', 'Marketing', 'Finance', 
           'IT', 'HR', 'Marketing', 'Finance', 'IT'],
    '연차': [3, 5, 8, 2, 6, 1, 4, 7, 3, 2],
    '연봉': [4500, 4000, 6000, 3500, 5000, 3000, 3800, 5500, 4200, 3200]
}

# DataFrame으로 변환 후 CSV로 저장
sample_df = pd.DataFrame(sample_data)
sample_df.to_csv('employee_data.csv', index=False, encoding='utf-8-sig')

# CSV 파일 읽기
df = pd.read_csv('employee_data.csv')
print("=== CSV에서 불러온 데이터 ===")
print(df)
```

## 4. 데이터 선택: loc[]과 iloc[] 완전 가이드

Pandas에서 데이터를 선택하는 가장 중요한 두 가지 방법입니다.

### 핵심 차이점

- **`iloc[]`**: **위치(position) 기반** 인덱싱 (숫자로만)
- **`loc[]`**: **라벨(label) 기반** 인덱싱 (인덱스명, 컬럼명으로)

### iloc[] - 위치 기반 선택

```python
print("=== iloc[] 위치 기반 선택 ===")

# 단일 행 선택 (첫 번째 행)
print("첫 번째 행:")
print(df.iloc[0])
print()

# 여러 행 선택 (처음 3개 행)
print("처음 3개 행:")
print(df.iloc[0:3])  # 0, 1, 2번 행 (3번 제외)
print()

# 특정 위치의 값 (2번째 행, 3번째 열)
print("2번째 행, 3번째 열 값:")
print(df.iloc[1, 2])  # 'IT'
print()

# 여러 행과 열 선택
print("0,2번째 행의 1,3번째 열:")
print(df.iloc[[0, 2], [1, 3]])
print()

# 슬라이싱으로 범위 선택
print("1~3번째 행, 1~2번째 열:")
print(df.iloc[1:4, 1:3])
```

### loc[] - 라벨 기반 선택

```python
print("=== loc[] 라벨 기반 선택 ===")

# 인덱스 라벨로 행 선택
print("인덱스 0번 행:")
print(df.loc[0])
print()

# 컬럼명으로 선택
print("이름과 연봉 컬럼:")
print(df.loc[:, ['이름', '연봉']])
print()

# 특정 행과 열 선택 (인덱스 1, 컬럼 '부서')
print("인덱스 1, 부서 컬럼:")
print(df.loc[1, '부서'])
print()

# 조건으로 선택 (가장 중요!)
print("연차가 5년 이상인 직원들:")
print(df.loc[df['연차'] >= 5])
print()

# 복합 조건
print("IT 부서이면서 연봉 4000 이상:")
print(df.loc[(df['부서'] == 'IT') & (df['연봉'] >= 4000)])
```

### 인덱스가 문자열인 경우의 차이

```python
# 인덱스를 이름으로 변경
df_named = df.set_index('이름')
print("=== 인덱스가 이름인 경우 ===")
print(df_named.head(3))
print()

# iloc은 여전히 위치로 접근
print("iloc[0] - 첫 번째 행:")
print(df_named.iloc[0])  # 김철수 행
print()

# loc은 인덱스 라벨로 접근
print("loc['김철수'] - 김철수 행:")
print(df_named.loc['김철수'])
print()

# 여러 이름으로 선택
print("김철수, 박민수 선택:")
print(df_named.loc[['김철수', '박민수']])
```

### 슬라이싱 차이점 (중요!)

```python
print("=== 슬라이싱 차이점 ===")

# iloc 슬라이싱 (끝 인덱스 제외)
print("iloc[1:3] - 1, 2번째 행:")
print(df.iloc[1:3])  # 인덱스 1, 2 (3 제외)
print()

# loc 슬라이싱 (끝 인덱스 포함)  
print("loc[1:3] - 1, 2, 3번째 행:")
print(df.loc[1:3])   # 인덱스 1, 2, 3 (3 포함)
```

### 실전 활용 예시

```python
# 데이터 탐색할 때
print("=== 실전 활용 ===")

# iloc 활용 - 데이터 미리보기
print("처음 3개 데이터:", df.iloc[:3].shape)
print("마지막 2개 데이터:", df.iloc[-2:].shape)
print("랜덤한 위치들:", df.iloc[[1, 3, 5]].shape)

# loc 활용 - 조건 기반 분석
it_employees = df.loc[df['부서'] == 'IT']
high_salary = df.loc[df['연봉'] >= 5000]
senior_it = df.loc[(df['부서'] == 'IT') & (df['연차'] >= 5)]

print(f"IT 부서 직원: {len(it_employees)}명")
print(f"고액 연봉자: {len(high_salary)}명") 
print(f"시니어 IT 직원: {len(senior_it)}명")
```

## 5. 조건에 맞는 데이터 필터링

### 단일 조건 필터링

```python
# 연봉이 4000 이상인 직원
high_salary = df.loc[df['연봉'] >= 4000]
print("=== 연봉 4000 이상인 직원 ===")
print(high_salary)

# IT 부서 직원들
it_employees = df.loc[df['부서'] == 'IT']
print("\n=== IT 부서 직원 ===")
print(it_employees)

# 연차가 5년 미만인 직원
junior_employees = df.loc[df['연차'] < 5]
print("\n=== 연차 5년 미만 직원 ===")
print(junior_employees)
```

### 복합 조건 필터링

```python
# IT 부서이면서 연봉이 4000 이상인 직원
it_high_salary = df.loc[(df['부서'] == 'IT') & (df['연봉'] >= 4000)]
print("=== IT 부서 & 연봉 4000 이상 ===")
print(it_high_salary)

# 연차가 3년 이상이거나 연봉이 5000 이상인 직원
senior_or_high_paid = df.loc[(df['연차'] >= 3) | (df['연봉'] >= 5000)]
print("\n=== 연차 3년 이상 OR 연봉 5000 이상 ===")
print(senior_or_high_paid)

# 특정 부서들만 선택
target_departments = df.loc[df['부서'].isin(['IT', 'Finance'])]
print("\n=== IT 또는 Finance 부서 ===")
print(target_departments)
```

## 6. 데이터 조작 기본 기능

### 열(Column) 선택

```python
# 단일 컬럼 선택
names = df['이름']
print("=== 이름 컬럼만 ===")
print(names)
print(type(names))  # pandas.core.series.Series

# 여러 컬럼 선택
basic_info = df[['이름', '부서', '연봉']]
print("\n=== 기본 정보만 ===")
print(basic_info)

# loc으로 컬럼 선택 (더 유연함)
basic_info_loc = df.loc[:, ['이름', '부서', '연봉']]
print("\n=== loc으로 컬럼 선택 ===")
print(basic_info_loc)
```

### 행(Row) 선택 비교

```python
# iloc으로 행 선택 (위치 기반)
print("=== iloc 행 선택 ===")
first_employee = df.iloc[0]  # 첫 번째 행
first_three = df.iloc[0:3]   # 0, 1, 2번 행
print("첫 번째 직원:")
print(first_employee)

# loc으로 행 선택 (조건 기반)
print("\n=== loc 행 선택 ===")
specific_employee = df.loc[df['이름'] == '김철수']
it_employees = df.loc[df['부서'] == 'IT']
print("김철수 정보:")
print(specific_employee)
```

### 데이터 정렬

```python
# 연봉 기준 오름차순 정렬
sorted_by_salary = df.sort_values('연봉')
print("=== 연봉 오름차순 정렬 ===")
print(sorted_by_salary)

# 연봉 기준 내림차순 정렬
sorted_by_salary_desc = df.sort_values('연봉', ascending=False)
print("\n=== 연봉 내림차순 정렬 ===")
print(sorted_by_salary_desc)

# 여러 컬럼 기준 정렬 (부서별로 먼저, 그다음 연봉으로)
multi_sorted = df.sort_values(['부서', '연봉'], ascending=[True, False])
print("\n=== 부서별, 연봉 내림차순 정렬 ===")
print(multi_sorted)
```

## 7. 그룹화 및 집계 분석

```python
# 부서별 통계
dept_stats = df.groupby('부서').agg({
    '연봉': ['mean', 'max', 'min', 'count'],
    '연차': 'mean'
})
print("=== 부서별 통계 ===")
print(dept_stats)

# 부서별 평균 연봉 (더 간단한 방법)
dept_avg_salary = df.groupby('부서')['연봉'].mean()
print("\n=== 부서별 평균 연봉 ===")
print(dept_avg_salary)

# 부서별 직원 수
dept_count = df['부서'].value_counts()
print("\n=== 부서별 직원 수 ===")
print(dept_count)
```

## 8. loc/iloc 언제 사용할까?

### iloc 사용 권장 상황

```python
# 1. 데이터 미리보기
print("처음 5개:", df.iloc[:5])
print("마지막 3개:", df.iloc[-3:])

# 2. 특정 위치 데이터 필요
middle_rows = df.iloc[2:5]  # 가운데 데이터

# 3. 랜덤 샘플링
import numpy as np
random_indices = np.random.choice(len(df), 3, replace=False)
random_sample = df.iloc[random_indices]

# 4. 순차적 데이터 처리
for i in range(len(df)):
    row = df.iloc[i]
    # 각 행 처리...
```

### loc 사용 권장 상황

```python
# 1. 조건 기반 필터링 (가장 중요!)
high_performers = df.loc[(df['연봉'] >= 5000) & (df['연차'] >= 5)]

# 2. 특정 컬럼만 필요할 때
essential_info = df.loc[:, ['이름', '부서', '연봉']]

# 3. 인덱스/컬럼명을 알고 있을 때
specific_data = df.loc[df['이름'] == '김철수', ['부서', '연봉']]

# 4. 데이터 수정할 때
df.loc[df['부서'] == 'IT', '보너스'] = 500  # IT 부서에 보너스 컬럼 추가
```
### loc/iloc 요약 정리

|구분|iloc[]|loc[]|
|---|---|---|
|**기준**|위치(숫자)|라벨(이름)|
|**인덱싱**|`df.iloc[0, 1]`|`df.loc[0, '컬럼명']`|
|**슬라이싱**|끝 제외 `[1:3]` → 1,2|끝 포함 `[1:3]` → 1,2,3|
|**주요 용도**|순서 기반 선택|조건 기반 선택|
|**예시**|`df.iloc[0:5]`|`df.loc[df['가격'] > 1000]`|

**기억하는 팁**:

- **i**loc = **i**nteger (정수 위치)
- **l**oc = **l**abel (라벨/이름)


## 9. 실습: 분석 목적에 맞는 테이블 작성

### 실습 1: 판매 데이터 분석

```python
# 판매 데이터 생성
sales_data = {
    '날짜': ['2024-01-01', '2024-01-02', '2024-01-03', '2024-01-04', '2024-01-05',
            '2024-01-06', '2024-01-07', '2024-01-08', '2024-01-09', '2024-01-10'],
    '상품': ['노트북', '마우스', '키보드', '노트북', '모니터', 
           '마우스', '키보드', '노트북', '모니터', '키보드'],
    '카테고리': ['전자제품', '액세서리', '액세서리', '전자제품', '전자제품',
              '액세서리', '액세서리', '전자제품', '전자제품', '액세서리'],
    '수량': [2, 5, 3, 1, 2, 8, 4, 1, 3, 6],
    '단가': [1000000, 30000, 80000, 1200000, 300000, 
           25000, 85000, 1100000, 280000, 90000],
    '판매원': ['김철수', '이영희', '김철수', '박민수', '이영희',
            '박민수', '김철수', '이영희', '박민수', '김철수']
}

sales_df = pd.DataFrame(sales_data)
sales_df['총액'] = sales_df['수량'] * sales_df['단가']  # 총 판매액 계산

print("=== 판매 데이터 ===")
print(sales_df)

# loc/iloc 활용한 분석
print("\n=== iloc 활용: 최근 5건 판매 ===")
recent_sales = sales_df.iloc[-5:]
print(recent_sales)

print("\n=== loc 활용: 고액 판매 건 ===")
high_value_sales = sales_df.loc[sales_df['총액'] >= 1000000]
print(high_value_sales)

# 분석 1: 상품별 총 판매액
product_sales = sales_df.groupby('상품').agg({
    '총액': 'sum',
    '수량': 'sum'
}).sort_values('총액', ascending=False)

print("\n=== 상품별 판매 실적 ===")
print(product_sales)

# 분석 2: 판매원별 실적
salesperson_performance = sales_df.groupby('판매원').agg({
    '총액': ['sum', 'mean'],
    '수량': 'sum'
}).round(0)

print("\n=== 판매원별 실적 ===")
print(salesperson_performance)

# loc으로 상위 판매원 찾기
top_salesperson = sales_df.groupby('판매원')['총액'].sum().idxmax()
top_sales_data = sales_df.loc[sales_df['판매원'] == top_salesperson]
print(f"\n=== 최고 판매원 {top_salesperson}의 판매 내역 ===")
print(top_sales_data)
```

### 실습 2: 고객 데이터 분석 (loc/iloc 중점)

```python
# 고객 데이터 생성
customer_data = {
    '고객ID': [1001, 1002, 1003, 1004, 1005, 1006, 1007, 1008, 1009, 1010],
    '이름': ['김고객', '이구매', '박주문', '최단골', '정신규', 
           '황단가', '강충성', '서이용', '윤재구', '조신입'],
    '연령': [25, 35, 45, 30, 28, 50, 40, 33, 27, 29],
    '성별': ['남', '여', '남', '여', '남', '여', '남', '여', '남', '여'],
    '지역': ['서울', '부산', '대구', '서울', '인천', '부산', '서울', '대구', '인천', '서울'],
    '구매횟수': [15, 8, 25, 30, 5, 20, 18, 12, 7, 10],
    '총구매금액': [1500000, 800000, 3200000, 4500000, 400000, 
                2800000, 2100000, 1200000, 650000, 950000]
}

customer_df = pd.DataFrame(customer_data)
customer_df['평균구매금액'] = customer_df['총구매금액'] / customer_df['구매횟수']

print("=== 고객 데이터 ===")
print(customer_df)

# iloc 활용 분석
print("\n=== iloc 활용 ===")
print("상위 3명 고객 (총구매금액 기준):")
top3_customers = customer_df.sort_values('총구매금액', ascending=False).iloc[:3]
print(top3_customers[['이름', '총구매금액']])

print("\n첫 절반 고객들의 평균 구매금액:")
first_half = customer_df.iloc[:len(customer_df)//2]
print(f"평균: {first_half['총구매금액'].mean():,.0f}원")

# loc 활용 분석
print("\n=== loc 활용 ===")
# VIP 고객 분석 (총 구매금액 200만원 이상)
vip_customers = customer_df.loc[customer_df['총구매금액'] >= 2000000]
print("VIP 고객 (구매금액 200만원 이상):")
print(vip_customers[['이름', '총구매금액', '구매횟수']])

# 서울 거주 30대 고객
seoul_30s = customer_df.loc[(customer_df['지역'] == '서울') & 
                           (customer_df['연령'] >= 30) & 
                           (customer_df['연령'] < 40)]
print(f"\n서울 거주 30대 고객: {len(seoul_30s)}명")
print(seoul_30s[['이름', '연령', '총구매금액']])

# 지역별 고객 분석
regional_analysis = customer_df.groupby('지역').agg({
    '고객ID': 'count',           # 고객 수
    '총구매금액': ['sum', 'mean'], # 총액, 평균
    '구매횟수': 'mean'            # 평균 구매횟수
})

print("\n=== 지역별 고객 분석 ===")
print(regional_analysis)

# 연령대별 분석
customer_df['연령대'] = pd.cut(customer_df['연령'], 
                          bins=[0, 30, 40, 100], 
                          labels=['20대', '30대', '40대+'])

age_analysis = customer_df.groupby('연령대').agg({
    '총구매금액': 'mean',
    '구매횟수': 'mean',
    '평균구매금액': 'mean'
}).round(0)

print("\n=== 연령대별 구매 패턴 ===")
print(age_analysis)
```

## 10. 데이터 저장

```python
# 분석 결과를 새로운 CSV 파일로 저장
vip_customers.to_csv('vip_customers.csv', index=False, encoding='utf-8-sig')
regional_analysis.to_csv('regional_analysis.csv', encoding='utf-8-sig')

print("분석 결과가 CSV 파일로 저장되었습니다!")
```

## 학습 정리

이번 실습을 통해 다음 내용을 학습했습니다:

1. **Pandas의 주요 특성**: 구조화된 데이터 처리, 다양한 파일 형식 지원
2. **DataFrame 개념**: 행과 열로 구성된 2차원 테이블 구조
3. **데이터 불러오기**: CSV 파일 읽기 및 DataFrame 생성
4. **loc/iloc 완전 이해**: 위치 기반 vs 라벨 기반 데이터 선택
5. **조건 필터링**: 단일/복합 조건을 사용한 데이터 선택
6. **분석용 테이블 작성**: 그룹화, 집계를 통한 의미있는 분석 결과 도출

Pandas의 loc과 iloc을 제대로 이해하면 데이터 분석이 훨씬 수월해집니다. 이 기초를 바탕으로 더 복잡한 데이터 분석과 시각화로 발전시킬 수 있습니다!
