#  기본 연산자/자료형

## 1. 기본 연산자

### 산술 연산자

```python
# 기본 산술 연산
a = 10
b = 3

print(a + b)    # 13 (덧셈)
print(a - b)    # 7  (뺄셈)
print(a * b)    # 30 (곱셈)
print(a / b)    # 3.333... (나눗셈)
print(a // b)   # 3  (몫)
print(a % b)    # 1  (나머지)
print(a ** b)   # 1000 (거듭제곱)
```

### 비교 연산자

```python
x = 5
y = 10

print(x == y)   # False (같음)
print(x != y)   # True  (다름)
print(x < y)    # True  (작음)
print(x > y)    # False (큼)
print(x <= y)   # True  (작거나 같음)
print(x >= y)   # False (크거나 같음)
```

### 논리 연산자

```python
a = True
b = False

print(a and b)  # False (둘 다 참일 때만 True)
print(a or b)   # True  (하나라도 참이면 True)
print(not a)    # False (참/거짓 반대)
```

### 할당 연산자

```python
x = 10
x += 5    # x = x + 5, 결과: 15
x -= 3    # x = x - 3, 결과: 12
x *= 2    # x = x * 2, 결과: 24
x /= 4    # x = x / 4, 결과: 6.0
```

## 2. 기본 자료형

### 숫자형 (Numeric)

```python
# 정수형 (int)
age = 25
count = -10

# 실수형 (float)
height = 175.5
temperature = -15.2

# 복소수형 (complex)
complex_num = 3 + 4j

print(type(age))        # <class 'int'>
print(type(height))     # <class 'float'>
```

### 문자열 (String)

```python
# 문자열 생성
name = "홍길동"
message = '안녕하세요'
long_text = """여러 줄
문자열입니다"""

# 문자열 연산
first_name = "김"
last_name = "철수"
full_name = first_name + last_name  # "김철수"

# 문자열 반복
greeting = "안녕" * 3  # "안녕안녕안녕"

# 문자열 인덱싱과 슬라이싱
text = "Python"
print(text[0])      # 'P'
print(text[-1])     # 'n'
print(text[0:3])    # 'Pyt'
```

### 불린 (Boolean)

```python
is_student = True
is_adult = False

# 불린 연산
result = is_student and is_adult  # False
print(type(result))  # <class 'bool'>
```

## 3. 컨테이너 자료형

### 리스트 (List) - 순서있고 변경가능

```python
# 리스트 생성
numbers = [1, 2, 3, 4, 5]
names = ["김철수", "이영희", "박민수"]
mixed = [1, "hello", 3.14, True]

# 리스트 조작
numbers.append(6)       # 끝에 추가
numbers.insert(0, 0)    # 특정 위치에 삽입
numbers.remove(3)       # 값으로 삭제
popped = numbers.pop()  # 마지막 요소 제거하고 반환

print(len(numbers))     # 리스트 길이
```

### 튜플 (Tuple) - 순서있고 변경불가능

```python
# 튜플 생성
coordinates = (10, 20)
colors = ("red", "green", "blue")
single_tuple = (42,)  # 단일 요소 튜플은 쉼표 필요

# 튜플은 수정 불가능
# coordinates[0] = 15  # 에러 발생

# 튜플 언패킹
x, y = coordinates
print(x, y)  # 10 20
```

### 딕셔너리 (Dictionary) - 키-값 쌍

```python
# 딕셔너리 생성
student = {
    "name": "김철수",
    "age": 20,
    "major": "컴퓨터공학"
}

# 딕셔너리 조작
student["grade"] = "A+"     # 새 키-값 추가
student["age"] = 21         # 값 수정
del student["major"]        # 키-값 삭제

# 딕셔너리 메서드
print(student.keys())       # 모든 키
print(student.values())     # 모든 값
print(student.items())      # 모든 키-값 쌍
```

### 집합 (Set) - 중복없는 데이터

```python
# 집합 생성
fruits = {"apple", "banana", "orange"}
numbers = set([1, 2, 3, 2, 1])  # {1, 2, 3} - 중복 제거

# 집합 연산
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1 | set2)  # 합집합: {1, 2, 3, 4, 5}
print(set1 & set2)  # 교집합: {3}
print(set1 - set2)  # 차집합: {1, 2}
```

## 4. 자료형 확인 및 변환

### 자료형 확인

```python
data = 42
print(type(data))           # <class 'int'>
print(isinstance(data, int)) # True
```

### 자료형 변환

```python
# 문자열 → 숫자
num_str = "123"
num_int = int(num_str)      # 123
num_float = float(num_str)  # 123.0

# 숫자 → 문자열
number = 456
str_num = str(number)       # "456"

# 리스트 → 튜플 → 리스트
my_list = [1, 2, 3]
my_tuple = tuple(my_list)   # (1, 2, 3)
back_to_list = list(my_tuple) # [1, 2, 3]
```



#  Formatting

## 1. 문자열 포매팅 개요

Python에서 문자열 포매팅은 변수나 값을 문자열에 삽입하는 방법입니다. 시대순으로 여러 방법이 있습니다.

### 포매팅 방법들의 발전사

1. **% 포매팅** (구식, Python 2 시대)
2. **str.format()** (Python 2.7/3.0+)
3. **f-string** (Python 3.6+, 현재 권장)

## 2. f-string (Formatted String Literals) - 가장 권장

### 기본 문법

```python
# 변수 삽입
name = "김철수"
age = 25
print(f"안녕하세요, 저는 {name}이고 {age}살입니다.")
# 출력: 안녕하세요, 저는 김철수이고 25살입니다.

# 표현식 사용 가능
x = 10
y = 20
print(f"{x} + {y} = {x + y}")
# 출력: 10 + 20 = 30

# 함수 호출도 가능
text = "python programming"
print(f"대문자로: {text.upper()}")
# 출력: 대문자로: PYTHON PROGRAMMING
```

### 숫자 포매팅

```python
# 소수점 자릿수 제한
pi = 3.141592653589793
print(f"파이 값: {pi:.2f}")        # 소수점 둘째자리까지
print(f"파이 값: {pi:.4f}")        # 소수점 넷째자리까지
# 출력: 파이 값: 3.14
# 출력: 파이 값: 3.1416

# 정수 자릿수 맞춤
number = 42
print(f"숫자: {number:5d}")        # 5자리 공간, 우측 정렬
print(f"숫자: {number:05d}")       # 5자리, 앞에 0 채움
# 출력: 숫자:    42
# 출력: 숫자: 00042

# 천 단위 구분자
large_number = 1234567
print(f"큰 수: {large_number:,}")
print(f"큰 수: {large_number:_}")  # 언더스코어 구분자
# 출력: 큰 수: 1,234,567
# 출력: 큰 수: 1_234_567
```

### 정렬과 패딩

```python
# 문자열 정렬
name = "Python"
print(f"좌측 정렬: '{name:<10}'")
print(f"우측 정렬: '{name:>10}'")
print(f"중앙 정렬: '{name:^10}'")
print(f"중앙 정렬(패딩): '{name:*^10}'")
# 출력: 좌측 정렬: 'Python    '
# 출력: 우측 정렬: '    Python'
# 출력: 중앙 정렬: '  Python  '
# 출력: 중앙 정렬(패딩): '**Python**'
```

### 진법 변환

```python
number = 255
print(f"10진수: {number}")
print(f"2진수: {number:b}")
print(f"8진수: {number:o}")
print(f"16진수: {number:x}")
print(f"16진수(대문자): {number:X}")
# 출력: 10진수: 255
# 출력: 2진수: 11111111
# 출력: 8진수: 377
# 출력: 16진수: ff
# 출력: 16진수(대문자): FF
```

### 퍼센트 표시

```python
ratio = 0.875
print(f"성공률: {ratio:.1%}")
print(f"성공률: {ratio:.2%}")
# 출력: 성공률: 87.5%
# 출력: 성공률: 87.50%
```

## 3. str.format() 메서드

### 기본 사용법

```python
# 위치 인덱스 사용
name = "이영희"
age = 30
print("안녕하세요, 저는 {}이고 {}살입니다.".format(name, age))
print("안녕하세요, 저는 {0}이고 {1}살입니다.".format(name, age))
print("안녕하세요, 저는 {1}이고 {0}살입니다.".format(age, name))  # 순서 바꾸기

# 키워드 인수 사용
print("안녕하세요, 저는 {name}이고 {age}살입니다.".format(name="박민수", age=28))
```

### 고급 포매팅

```python
# 딕셔너리 사용
person = {"name": "홍길동", "age": 35, "job": "개발자"}
print("이름: {name}, 나이: {age}, 직업: {job}".format(**person))

# 리스트/튜플 사용
data = ["Python", "Programming", 2023]
print("언어: {0[0]}, 분야: {0[1]}, 년도: {0[2]}".format(data))
```

## 4. % 포매팅 (구식, 참고용)

```python
# 기본 사용법 (권장하지 않음, 참고용만)
name = "김개발"
age = 27
print("이름: %s, 나이: %d" % (name, age))

# 딕셔너리 사용
print("이름: %(name)s, 나이: %(age)d" % {"name": name, "age": age})
```

## 5. 실용적인 포매팅 예제

### 테이블 형태 출력

```python
# 학생 성적표
students = [
    {"name": "김철수", "korean": 85, "english": 92, "math": 78},
    {"name": "이영희", "korean": 95, "english": 87, "math": 91},
    {"name": "박민수", "korean": 76, "english": 84, "math": 89}
]

print(f"{'이름':^8} {'국어':>6} {'영어':>6} {'수학':>6} {'평균':>8}")
print("-" * 40)

for student in students:
    name = student["name"]
    korean = student["korean"]
    english = student["english"]
    math = student["math"]
    average = (korean + english + math) / 3
    
    print(f"{name:^8} {korean:>6} {english:>6} {math:>6} {average:>8.1f}")
```

### 진행률 표시

```python
def show_progress(current, total, bar_length=20):
    progress = current / total
    filled_length = int(bar_length * progress)
    bar = "█" * filled_length + "░" * (bar_length - filled_length)
    
    print(f"\r진행률: |{bar}| {progress:.1%} ({current}/{total})", end="")

# 사용 예제
import time
for i in range(101):
    show_progress(i, 100)
    time.sleep(0.1)  # 실제로는 작업 시간
print()  # 완료 후 줄바꿈
```

### 파일 크기 포매팅

```python
def format_file_size(bytes_size):
    """바이트를 읽기 쉬운 형태로 변환"""
    for unit in ['B', 'KB', 'MB', 'GB', 'TB']:
        if bytes_size < 1024.0:
            return f"{bytes_size:.1f} {unit}"
        bytes_size /= 1024.0
    return f"{bytes_size:.1f} PB"

# 사용 예제
file_sizes = [1024, 1048576, 1073741824, 1099511627776]
for size in file_sizes:
    print(f"파일 크기: {format_file_size(size)}")
```

### 시간 포매팅

```python
import datetime

now = datetime.datetime.now()
print(f"현재 시간: {now:%Y-%m-%d %H:%M:%S}")
print(f"날짜만: {now:%Y년 %m월 %d일}")
print(f"시간만: {now:%H시 %M분 %S초}")

# 요일 표시
weekdays = ["월", "화", "수", "목", "금", "토", "일"]
weekday = weekdays[now.weekday()]
print(f"오늘은 {weekday}요일입니다.")
```

### 금액 포매팅

```python
def format_currency(amount, currency="원"):
    """금액을 통화 형식으로 포매팅"""
    return f"{amount:,}{currency}"

# 사용 예제
prices = [1000, 15000, 250000, 1500000]
for price in prices:
    print(f"가격: {format_currency(price)}")

# 달러 표시
print(f"Price: ${15.99:.2f}")
print(f"Price: ${1234.5:,.2f}")
```

## 6. 다양한 데이터 타입 포매팅

### 리스트와 딕셔너리

```python
# 리스트 포매팅
numbers = [1, 2, 3, 4, 5]
print(f"숫자들: {numbers}")
print(f"숫자들 (문자열): {', '.join(map(str, numbers))}")

# 딕셔너리 깔끔하게 출력
config = {
    "host": "localhost",
    "port": 8080,
    "debug": True,
    "timeout": 30
}

print("=== 설정 정보 ===")
for key, value in config.items():
    print(f"{key:.<15}: {value}")
```

### 조건부 포매팅

```python
def format_grade(score):
    if score >= 90:
        grade = "A"
    elif score >= 80:
        grade = "B"
    elif score >= 70:
        grade = "C"
    else:
        grade = "F"
    
    return f"점수: {score:3d}점 (등급: {grade})"

# 사용
scores = [95, 85, 75, 65]
for score in scores:
    print(format_grade(score))
```

### 멀티라인 포매팅

```python
# 여러 줄 문자열 포매팅
name = "홍길동"
age = 30
job = "개발자"
city = "서울"

profile = f"""
===== 프로필 =====
이름: {name}
나이: {age}세
직업: {job}
거주지: {city}
==================
"""
print(profile)

# 들여쓰기 있는 포매팅
def create_html_card(title, content):
    return f"""
    <div class="card">
        <h2>{title}</h2>
        <p>{content}</p>
    </div>
    """

card = create_html_card("Python 학습", "f-string을 배우고 있습니다.")
print(card)
```

## 7. 포매팅 방법별 성능 비교

```python
import timeit

name = "Python"
age = 10

# f-string (가장 빠름)
def f_string():
    return f"Hello, {name}! You are {age} years old."

# str.format()
def str_format():
    return "Hello, {}! You are {} years old.".format(name, age)

# % 포매팅
def percent_format():
    return "Hello, %s! You are %d years old." % (name, age)

# 성능 테스트 (실제 실행하면 시간 측정 가능)
print("f-string이 가장 빠르고 가독성이 좋습니다!")
```

## 8. 포매팅 권장사항

### 언제 어떤 방법을 사용할까?

1. **f-string 사용 (Python 3.6+)**: 대부분의 경우 권장
    
    - 가독성이 좋음
    - 성능이 빠름
    - 표현식 사용 가능
2. **str.format() 사용**:
    
    - 템플릿을 미리 정의할 때
    - Python 3.6 미만 버전 지원
3. **% 포매팅**:
    
    - 레거시 코드 유지보수
    - 로깅에서 사용 (logging 모듈과의 호환성)

### 좋은 포매팅 예제

```python
# 명확하고 읽기 쉬운 포매팅
def display_user_info(user):
    return (f"사용자: {user['name']:<10} | "
            f"이메일: {user['email']:<20} | "
            f"가입일: {user['joined']:%Y-%m-%d}")

# 재사용 가능한 템플릿
EMAIL_TEMPLATE = """
안녕하세요 {name}님,

{message}

감사합니다.
{sender}
"""

def send_email(name, message, sender="관리자"):
    return EMAIL_TEMPLATE.format(name=name, message=message, sender=sender)
```

Python의 문자열 포매팅은 데이터를 사용자 친화적으로 표시하는 핵심 기능입니다. f-string을 중심으로 다양한 포매팅 옵션들을 익혀두시면 더 전문적이고 읽기 쉬운 코드를 작성할 수 있습니다! 

#  반복문

## 1. for 문

### 기본 문법

```python
# 리스트를 이용한 반복
fruits = ["사과", "바나나", "오렌지"]
for fruit in fruits:
    print(f"좋아하는 과일: {fruit}")

# 출력:
# 좋아하는 과일: 사과
# 좋아하는 과일: 바나나
# 좋아하는 과일: 오렌지
```

### range() 함수와 함께 사용

```python
# range(n): 0부터 n-1까지
for i in range(5):
    print(f"숫자: {i}")
# 출력: 0, 1, 2, 3, 4

# range(start, stop): start부터 stop-1까지
for i in range(2, 8):
    print(f"숫자: {i}")
# 출력: 2, 3, 4, 5, 6, 7

# range(start, stop, step): 시작, 끝, 간격
for i in range(0, 10, 2):
    print(f"짝수: {i}")
# 출력: 0, 2, 4, 6, 8

# 역순으로 반복
for i in range(10, 0, -1):
    print(f"카운트다운: {i}")
# 출력: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

### 다양한 데이터 타입 반복

```python
# 문자열 반복
for char in "Python":
    print(f"문자: {char}")

# 딕셔너리 반복
student = {"이름": "김철수", "나이": 20, "전공": "컴퓨터공학"}

# 키만 반복
for key in student:
    print(f"키: {key}")

# 키와 값 함께 반복
for key, value in student.items():
    print(f"{key}: {value}")

# 값만 반복
for value in student.values():
    print(f"값: {value}")
```

### enumerate() 함수

```python
# 인덱스와 값을 함께 얻기
subjects = ["수학", "영어", "과학", "사회"]

for index, subject in enumerate(subjects):
    print(f"{index + 1}번째 과목: {subject}")

# 시작 인덱스 지정
for index, subject in enumerate(subjects, start=1):
    print(f"{index}번째 과목: {subject}")
```

### zip() 함수

```python
# 여러 리스트를 동시에 반복
names = ["김철수", "이영희", "박민수"]
ages = [25, 30, 28]
cities = ["서울", "부산", "대구"]

for name, age, city in zip(names, ages, cities):
    print(f"{name}({age}세)는 {city}에 살고 있습니다.")
```

## 2. while 문

### 기본 문법

```python
# 조건이 True인 동안 반복
count = 0
while count < 5:
    print(f"카운트: {count}")
    count += 1  # count = count + 1

print("반복 완료!")
```

### 사용자 입력과 while문

```python
# 특정 입력이 들어올 때까지 반복
while True:
    user_input = input("종료하려면 'quit'를 입력하세요: ")
    if user_input.lower() == 'quit':
        print("프로그램을 종료합니다.")
        break
    else:
        print(f"입력하신 내용: {user_input}")
```

### 조건부 while문

```python
# 숫자 맞추기 게임
import random

secret_number = random.randint(1, 100)
attempts = 0
max_attempts = 7

while attempts < max_attempts:
    guess = int(input("1-100 사이의 숫자를 맞춰보세요: "))
    attempts += 1
    
    if guess == secret_number:
        print(f"정답! {attempts}번만에 맞췄습니다.")
        break
    elif guess < secret_number:
        print("더 큰 수입니다.")
    else:
        print("더 작은 수입니다.")
    
    print(f"남은 기회: {max_attempts - attempts}번")
else:
    print(f"아쉽습니다. 정답은 {secret_number}였습니다.")
```

## 3. 반복문 제어

### break문 - 반복문 즉시 종료

```python
# for문에서 break
numbers = [1, 3, 5, 8, 10, 12]
for num in numbers:
    if num % 2 == 0:  # 짝수를 찾으면
        print(f"첫 번째 짝수를 찾았습니다: {num}")
        break
    print(f"홀수입니다: {num}")

# while문에서 break
count = 0
while True:
    if count >= 3:
        break
    print(f"무한 루프 {count}")
    count += 1
```

### continue문 - 현재 반복을 건너뛰기

```python
# 홀수만 출력하기
for i in range(1, 11):
    if i % 2 == 0:  # 짝수면 건너뛰기
        continue
    print(f"홀수: {i}")

# 특정 조건에서 continue
scores = [85, 92, 78, 96, 88, 45, 91]
passing_scores = []

for score in scores:
    if score < 80:  # 80점 미만은 건너뛰기
        continue
    passing_scores.append(score)
    print(f"합격 점수: {score}")

print(f"합격한 점수들: {passing_scores}")
```

### else절과 함께 사용

```python
# for-else: 반복문이 정상적으로 완료되었을 때 실행
numbers = [1, 3, 5, 7, 9]
target = 6

for num in numbers:
    if num == target:
        print(f"{target}을 찾았습니다!")
        break
else:
    print(f"{target}을 찾지 못했습니다.")

# while-else: while 조건이 False가 되어 종료될 때 실행
count = 0
while count < 3:
    print(f"카운트: {count}")
    count += 1
else:
    print("while문이 정상 완료되었습니다.")
```

## 4. 중첩 반복문

### 이중 for문

```python
# 구구단 출력
print("=== 구구단 ===")
for i in range(2, 10):
    print(f"\n[{i}단]")
    for j in range(1, 10):
        result = i * j
        print(f"{i} × {j} = {result}")

# 별 패턴 만들기
print("\n=== 별 패턴 ===")
for i in range(1, 6):
    for j in range(i):
        print("★", end="")
    print()  # 줄바꿈
```

### 2차원 리스트 처리

```python
# 2차원 리스트 생성
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# 모든 요소 출력
print("행렬의 모든 요소:")
for i in range(len(matrix)):
    for j in range(len(matrix[i])):
        print(f"matrix[{i}][{j}] = {matrix[i][j]}")

# 더 간단한 방법
print("\n간단한 방법:")
for row in matrix:
    for element in row:
        print(element, end=" ")
    print()  # 줄바꿈
```

## 5. 실용적인 반복문 예제

### 리스트 컴프리헨션 (List Comprehension)

```python
# 기본 for문
squares = []
for i in range(1, 6):
    squares.append(i ** 2)
print(squares)  # [1, 4, 9, 16, 25]

# 리스트 컴프리헨션으로 간단히
squares = [i ** 2 for i in range(1, 6)]
print(squares)  # [1, 4, 9, 16, 25]

# 조건부 리스트 컴프리헨션
even_squares = [i ** 2 for i in range(1, 11) if i % 2 == 0]
print(even_squares)  # [4, 16, 36, 64, 100]
```

### 파일 처리

```python
# 파일의 각 줄 처리 (예제)
filename = "data.txt"
try:
    with open(filename, 'r', encoding='utf-8') as file:
        line_count = 0
        for line in file:
            line_count += 1
            print(f"줄 {line_count}: {line.strip()}")
except FileNotFoundError:
    print(f"{filename} 파일을 찾을 수 없습니다.")
```

### 데이터 집계

```python
# 성적 통계 계산
students = [
    {"name": "김철수", "scores": [85, 92, 78]},
    {"name": "이영희", "scores": [95, 87, 91]},
    {"name": "박민수", "scores": [76, 84, 89]}
]

print("=== 학생별 성적 통계 ===")
for student in students:
    name = student["name"]
    scores = student["scores"]
    
    total = 0
    for score in scores:
        total += score
    
    average = total / len(scores)
    print(f"{name}: 총점 {total}, 평균 {average:.1f}")
```

### 메뉴 시스템

```python
def show_menu():
    print("\n=== 계산기 메뉴 ===")
    print("1. 덧셈")
    print("2. 뺄셈") 
    print("3. 곱셈")
    print("4. 나눗셈")
    print("0. 종료")

def calculator():
    while True:
        show_menu()
        choice = input("메뉴를 선택하세요: ")
        
        if choice == '0':
            print("계산기를 종료합니다.")
            break
        elif choice in ['1', '2', '3', '4']:
            try:
                a = float(input("첫 번째 숫자: "))
                b = float(input("두 번째 숫자: "))
                
                if choice == '1':
                    result = a + b
                    print(f"결과: {a} + {b} = {result}")
                elif choice == '2':
                    result = a - b
                    print(f"결과: {a} - {b} = {result}")
                elif choice == '3':
                    result = a * b
                    print(f"결과: {a} × {b} = {result}")
                elif choice == '4':
                    if b != 0:
                        result = a / b
                        print(f"결과: {a} ÷ {b} = {result}")
                    else:
                        print("0으로 나눌 수 없습니다.")
            except ValueError:
                print("올바른 숫자를 입력해주세요.")
        else:
            print("잘못된 선택입니다. 다시 선택해주세요.")

# calculator()  # 실행하려면 주석 해제
```

## 6. 반복문 성능 최적화 팁

```python
# 리스트 대신 제너레이터 사용 (메모리 효율적)
def number_generator(n):
    for i in range(n):
        yield i ** 2

# 큰 데이터 처리 시 유용
for square in number_generator(1000000):
    if square > 100:
        break
    print(square)

# enumerate 대신 range(len()) 피하기
# 좋지 않은 방법
items = ['a', 'b', 'c', 'd']
for i in range(len(items)):
    print(f"{i}: {items[i]}")

# 좋은 방법
for i, item in enumerate(items):
    print(f"{i}: {item}")
```

반복문은 프로그래밍에서 가장 중요한 제어 구조 중 하나입니다. 데이터 처리, 사용자 인터페이스, 알고리즘 구현 등 거의 모든 프로그램에서 사용되므로 다양한 패턴과 활용법을 익혀두시면 매우 유용합니다!


# 조건문 

## 1. 조건문 개요

조건문은 특정 조건에 따라 코드의 실행 흐름을 제어하는 구문입니다. Python에서는 `if`, `elif`, `else` 키워드를 사용합니다.

## 2. 기본 if문

### 기본 문법

```python
# 기본 if문
age = 20
if age >= 18:
    print("성인입니다.")
    print("투표할 수 있습니다.")

# 조건이 거짓일 때는 실행되지 않음
score = 65
if score >= 90:
    print("A등급입니다.")  # 실행되지 않음
```

### 들여쓰기 중요성

```python
# 올바른 들여쓰기 (4칸 공백 또는 탭)
temperature = 30
if temperature > 25:
    print("더워요!")
    print("에어컨을 켜세요.")

# 잘못된 들여쓰기 - 에러 발생
# if temperature > 25:
# print("더워요!")  # IndentationError 발생
```

## 3. if-else문

### 기본 if-else

```python
# 두 가지 경우로 분기
age = 16
if age >= 18:
    print("성인입니다.")
else:
    print("미성년자입니다.")

# 숫자 판별
number = 7
if number % 2 == 0:
    print(f"{number}는 짝수입니다.")
else:
    print(f"{number}는 홀수입니다.")
```

### 삼항 연산자 (조건부 표현식)

```python
# 기본 if-else
age = 20
if age >= 18:
    status = "성인"
else:
    status = "미성년자"

# 삼항 연산자로 간단히
age = 20
status = "성인" if age >= 18 else "미성년자"
print(status)

# 더 복잡한 예제
score = 85
grade = "합격" if score >= 60 else "불합격"
print(f"점수 {score}: {grade}")
```

## 4. elif문 (다중 조건)

### 기본 elif 사용법

```python
# 성적 등급 계산
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"점수 {score}점: {grade}등급")
```

### 복잡한 다중 조건

```python
# 계절 판별
month = 7

if month in [12, 1, 2]:
    season = "겨울"
elif month in [3, 4, 5]:
    season = "봄"
elif month in [6, 7, 8]:
    season = "여름"
elif month in [9, 10, 11]:
    season = "가을"
else:
    season = "잘못된 월"

print(f"{month}월은 {season}입니다.")
```

## 5. 논리 연산자와 조건문

### and, or, not 사용

```python
# and: 모든 조건이 참일 때
age = 25
has_license = True

if age >= 18 and has_license:
    print("운전할 수 있습니다.")
else:
    print("운전할 수 없습니다.")

# or: 하나 이상의 조건이 참일 때
weather = "비"
if weather == "비" or weather == "눈":
    print("우산을 챙기세요.")

# not: 조건을 반대로
is_weekend = False
if not is_weekend:
    print("평일입니다. 일해야 해요.")
```

### 복합 조건

```python
# 복합 조건 예제
temperature = 28
humidity = 75
is_sunny = True

if temperature > 25 and humidity > 60 and is_sunny:
    print("덥고 습하고 맑은 날씨입니다.")
elif temperature > 25 and not is_sunny:
    print("덥지만 흐린 날씨입니다.")
elif temperature <= 25 and is_sunny:
    print("시원하고 맑은 날씨입니다.")
else:
    print("쌀쌀하고 흐린 날씨입니다.")
```

## 6. 중첩 if문

### 기본 중첩 구조

```python
# 중첩 if문
age = 25
has_job = True
salary = 3000

if age >= 18:
    print("성인입니다.")
    if has_job:
        print("직업이 있습니다.")
        if salary >= 2500:
            print("대출 신청이 가능합니다.")
        else:
            print("소득이 부족합니다.")
    else:
        print("직업이 없습니다.")
else:
    print("미성년자입니다.")
```

### 회원 등급 시스템

```python
# 회원 등급 판별
years_of_membership = 5
total_purchases = 150000
is_premium = True

if years_of_membership >= 3:
    if total_purchases >= 100000:
        if is_premium:
            grade = "다이아몬드"
        else:
            grade = "골드"
    else:
        grade = "실버"
else:
    if total_purchases >= 50000:
        grade = "브론즈"
    else:
        grade = "일반"

print(f"회원 등급: {grade}")
```

## 7. 조건문에서 사용하는 다양한 표현

### in 연산자

```python
# 리스트, 튜플, 문자열에서 포함 여부 확인
fruits = ["사과", "바나나", "오렌지"]
fruit = "사과"

if fruit in fruits:
    print(f"{fruit}가 목록에 있습니다.")

# 숫자 범위 확인
numbers = [1, 3, 5, 7, 9]
num = 5

if num in numbers:
    print(f"{num}는 홀수 목록에 있습니다.")

# 문자열에서 부분 문자열 확인
email = "user@example.com"
if "@" in email and ".com" in email:
    print("유효한 이메일 형식입니다.")
```

### range 함수와 조건문

```python
# 점수 범위별 등급
score = 85

if score in range(90, 101):  # 90-100
    grade = "A"
elif score in range(80, 90):  # 80-89
    grade = "B"
elif score in range(70, 80):  # 70-79
    grade = "C"
elif score in range(60, 70):  # 60-69
    grade = "D"
else:
    grade = "F"

print(f"점수 {score}: {grade}등급")
```

### 문자열 메서드와 조건문

```python
# 문자열 검증
username = "user123"

if username.isalnum():  # 알파벳과 숫자만
    print("유효한 사용자명입니다.")
else:
    print("사용자명에 특수문자가 포함되어 있습니다.")

# 비밀번호 강도 체크
password = "MyPassword123!"

if len(password) >= 8:
    if password.islower():
        strength = "약함 (소문자만)"
    elif password.isupper():
        strength = "약함 (대문자만)"
    elif password.isdigit():
        strength = "약함 (숫자만)"
    else:
        strength = "강함"
else:
    strength = "약함 (너무 짧음)"

print(f"비밀번호 강도: {strength}")
```

## 8. 실용적인 조건문 예제

### 사용자 인증 시스템

```python
def authenticate_user(username, password):
    """사용자 인증 함수"""
    # 가상의 사용자 데이터베이스
    users = {
        "admin": "admin123",
        "user1": "password1",
        "user2": "password2"
    }
    
    if username in users:
        if users[username] == password:
            return "로그인 성공"
        else:
            return "비밀번호가 틀렸습니다"
    else:
        return "존재하지 않는 사용자입니다"

# 사용 예제
result = authenticate_user("admin", "admin123")
print(result)
```

### 쇼핑몰 할인 시스템

```python
def calculate_discount(total_amount, is_member, coupon_code=None):
    """할인 계산 함수"""
    discount_rate = 0
    discount_reason = []
    
    # 회원 할인
    if is_member:
        discount_rate += 0.1  # 10%
        discount_reason.append("회원 할인 10%")
    
    # 쿠폰 할인
    if coupon_code:
        if coupon_code == "WELCOME":
            discount_rate += 0.05  # 5%
            discount_reason.append("신규 쿠폰 5%")
        elif coupon_code == "SUMMER":
            discount_rate += 0.15  # 15%
            discount_reason.append("여름 쿠폰 15%")
    
    # 구매 금액별 추가 할인
    if total_amount >= 100000:
        discount_rate += 0.05  # 5%
        discount_reason.append("10만원 이상 구매 5%")
    elif total_amount >= 50000:
        discount_rate += 0.03  # 3%
        discount_reason.append("5만원 이상 구매 3%")
    
    # 최대 할인율 제한
    if discount_rate > 0.3:  # 30%
        discount_rate = 0.3
        discount_reason.append("(최대 할인 30% 적용)")
    
    discount_amount = total_amount * discount_rate
    final_amount = total_amount - discount_amount
    
    return {
        "원가": total_amount,
        "할인금액": int(discount_amount),
        "최종금액": int(final_amount),
        "할인사유": ", ".join(discount_reason)
    }

# 사용 예제
result = calculate_discount(80000, True, "SUMMER")
print(f"원가: {result['원가']:,}원")
print(f"할인: {result['할인금액']:,}원 ({result['할인사유']})")
print(f"최종: {result['최종금액']:,}원")
```

### 학생 성적 관리 시스템

```python
class StudentGradeManager:
    def __init__(self):
        self.students = {}
    
    def add_student(self, name, scores):
        """학생 추가"""
        self.students[name] = scores
    
    def calculate_grade(self, average):
        """평균 점수로 등급 계산"""
        if average >= 95:
            return "A+"
        elif average >= 90:
            return "A"
        elif average >= 85:
            return "B+"
        elif average >= 80:
            return "B"
        elif average >= 75:
            return "C+"
        elif average >= 70:
            return "C"
        elif average >= 65:
            return "D+"
        elif average >= 60:
            return "D"
        else:
            return "F"
    
    def get_student_report(self, name):
        """학생 성적 리포트"""
        if name not in self.students:
            return f"{name} 학생을 찾을 수 없습니다."
        
        scores = self.students[name]
        average = sum(scores) / len(scores)
        grade = self.calculate_grade(average)
        
        # 성적 상태 판별
        if average >= 90:
            status = "우수"
        elif average >= 80:
            status = "양호"
        elif average >= 70:
            status = "보통"
        elif average >= 60:
            status = "주의"
        else:
            status = "경고"
        
        return f"""
=== {name} 학생 성적표 ===
과목별 점수: {scores}
평균 점수: {average:.1f}
등급: {grade}
상태: {status}
{"장학금 대상" if average >= 95 else ""}
        """

# 사용 예제
manager = StudentGradeManager()
manager.add_student("김철수", [85, 92, 78, 88, 90])
manager.add_student("이영희", [95, 98, 92, 96, 94])

print(manager.get_student_report("김철수"))
print(manager.get_student_report("이영희"))
```

### 게임 캐릭터 상태 시스템

```python
class GameCharacter:
    def __init__(self, name, level=1, hp=100, mp=50):
        self.name = name
        self.level = level
        self.hp = hp
        self.max_hp = hp
        self.mp = mp
        self.max_mp = mp
    
    def get_status_message(self):
        """캐릭터 상태 메시지"""
        messages = []
        
        # HP 상태 체크
        hp_ratio = self.hp / self.max_hp
        if hp_ratio <= 0.1:
            messages.append("🔴 위험! HP가 매우 낮습니다!")
        elif hp_ratio <= 0.3:
            messages.append("🟡 주의! HP가 낮습니다.")
        elif hp_ratio >= 1.0:
            messages.append("💚 HP가 가득합니다.")
        
        # MP 상태 체크
        mp_ratio = self.mp / self.max_mp
        if mp_ratio <= 0.1:
            messages.append("🔵 MP가 거의 없습니다!")
        elif mp_ratio <= 0.3:
            messages.append("🟣 MP가 부족합니다.")
        
        # 레벨별 상태
        if self.level >= 50:
            messages.append("⭐ 고레벨 캐릭터입니다!")
        elif self.level >= 20:
            messages.append("✨ 중급 캐릭터입니다.")
        
        return messages
    
    def can_cast_spell(self, mp_cost):
        """마법 사용 가능 여부"""
        if self.mp >= mp_cost:
            if self.hp > 0:
                return True, "마법을 사용할 수 있습니다."
            else:
                return False, "HP가 0이므로 마법을 사용할 수 없습니다."
        else:
            return False, f"MP가 부족합니다. (필요: {mp_cost}, 보유: {self.mp})"

# 사용 예제
character = GameCharacter("마법사", level=25, hp=30, mp=10)

print(f"=== {character.name} 상태 ===")
print(f"레벨: {character.level}")
print(f"HP: {character.hp}/{character.max_hp}")
print(f"MP: {character.mp}/{character.max_mp}")

# 상태 메시지
status_messages = character.get_status_message()
for message in status_messages:
    print(message)

# 마법 사용 체크
can_cast, message = character.can_cast_spell(15)
print(f"\n마법 사용 가능: {message}")
```

## 9. 조건문 최적화 팁

### 조건문 순서 최적화

```python
# 나쁜 예: 자주 발생하지 않는 조건을 먼저 체크
def check_user_type_bad(user_level):
    if user_level == "admin":  # 드물게 발생
        return "관리자"
    elif user_level == "premium":  # 가끔 발생
        return "프리미엄 회원"
    elif user_level == "regular":  # 자주 발생
        return "일반 회원"
    else:
        return "게스트"

# 좋은 예: 자주 발생하는 조건을 먼저 체크
def check_user_type_good(user_level):
    if user_level == "regular":  # 자주 발생
        return "일반 회원"
    elif user_level == "premium":  # 가끔 발생
        return "프리미엄 회원"
    elif user_level == "admin":  # 드물게 발생
        return "관리자"
    else:
        return "게스트"
```

### 딕셔너리를 활용한 조건문 대체

```python
# 긴 if-elif 체인
def get_grade_verbose(score):
    if score >= 95:
        return "A+"
    elif score >= 90:
        return "A"
    elif score >= 85:
        return "B+"
    elif score >= 80:
        return "B"
    elif score >= 75:
        return "C+"
    elif score >= 70:
        return "C"
    else:
        return "F"

# 자료형과 함수를 활용한 깔끔한 방법
def get_grade_clean(score):
    grade_ranges = [
        (95, "A+"), (90, "A"), (85, "B+"), 
        (80, "B"), (75, "C+"), (70, "C")
    ]
    
    for min_score, grade in grade_ranges:
        if score >= min_score:
            return grade
    return "F"

# 더 간단한 방법 (작은 범위에서)
def get_day_type(day):
    day_types = {
        "월": "평일", "화": "평일", "수": "평일", 
        "목": "평일", "금": "평일",
        "토": "주말", "일": "주말"
    }
    return day_types.get(day, "잘못된 요일")
```

조건문은 프로그램의 논리를 구성하는 핵심 요소입니다. 명확하고 효율적인 조건문을 작성하면 코드의 가독성과 성능을 모두 향상시킬 수 있습니다. 다양한 상황에서 적절한 조건문 구조를 선택하는 것이 중요합니다!


# 사용자 정의 함수
## 함수의 기본 구조

```python
def 함수명(매개변수):
    """함수 설명 (선택사항)"""
    실행할 코드
    return 반환값  # 선택사항
```

## 1. 가장 간단한 함수

```python
def greet():
    print("안녕하세요!")

# 함수 호출
greet()  # 출력: 안녕하세요!
```

## 2. 매개변수가 있는 함수

```python
def greet_person(name):
    print(f"안녕하세요, {name}님!")

greet_person("김철수")  # 출력: 안녕하세요, 김철수님!
```

## 3. 반환값이 있는 함수

```python
def add_numbers(a, b):
    result = a + b
    return result

# 또는 더 간단하게
def add_numbers(a, b):
    return a + b

sum_result = add_numbers(5, 3)
print(sum_result)  # 출력: 8
```

## 4. 데이터 분석에 유용한 함수 예제

### 기본 통계 계산 함수

```python
def calculate_mean(numbers):
    """숫자 리스트의 평균을 계산하는 함수"""
    total = sum(numbers)
    count = len(numbers)
    return total / count

data = [10, 20, 30, 40, 50]
mean = calculate_mean(data)
print(f"평균: {mean}")  # 출력: 평균: 30.0
```

### 데이터 정제 함수

```python
def remove_outliers(data, threshold=2):
    """평균에서 threshold 표준편차 이상 떨어진 값들을 제거"""
    import statistics
    
    mean = statistics.mean(data)
    std = statistics.stdev(data)
    
    filtered_data = []
    for value in data:
        if abs(value - mean) <= threshold * std:
            filtered_data.append(value)
    
    return filtered_data

data = [1, 2, 3, 4, 5, 100, 6, 7, 8, 9]
clean_data = remove_outliers(data)
print(clean_data)  # [1, 2, 3, 4, 5, 6, 7, 8, 9] (100이 제거됨)
```

## 5. 기본값을 가진 매개변수

```python
def analyze_data(data, show_details=True):
    mean = sum(data) / len(data)
    
    if show_details:
        print(f"데이터 개수: {len(data)}")
        print(f"최댓값: {max(data)}")
        print(f"최솟값: {min(data)}")
    
    return mean

data = [1, 2, 3, 4, 5]
result1 = analyze_data(data)          # show_details=True (기본값)
result2 = analyze_data(data, False)   # show_details=False
```

## 6. 여러 값을 반환하는 함수

```python
def get_statistics(data):
    """데이터의 기본 통계량을 반환"""
    mean = sum(data) / len(data)
    maximum = max(data)
    minimum = min(data)
    
    return mean, maximum, minimum

data = [10, 20, 30, 40, 50]
avg, max_val, min_val = get_statistics(data)

print(f"평균: {avg}, 최댓값: {max_val}, 최솟값: {min_val}")
```

## 7. 가변 인수 함수

```python
def calculate_total(*numbers):
    """여러 개의 숫자를 받아서 합계를 계산"""
    return sum(numbers)

result1 = calculate_total(1, 2, 3)
result2 = calculate_total(1, 2, 3, 4, 5, 6)
print(result1)  # 6
print(result2)  # 21
```

## 실습 예제

데이터 분석에서 자주 사용할 수 있는 함수를 만들어보세요:

```python
def data_summary(data):
    """데이터의 요약 통계를 출력하는 함수"""
    if not data:  # 빈 리스트 체크
        print("데이터가 없습니다.")
        return None
    
    count = len(data)
    total = sum(data)
    mean = total / count
    maximum = max(data)
    minimum = min(data)
    
    print("=== 데이터 요약 ===")
    print(f"데이터 개수: {count}")
    print(f"합계: {total}")
    print(f"평균: {mean:.2f}")
    print(f"최댓값: {maximum}")
    print(f"최솟값: {minimum}")
    
    return {"count": count, "mean": mean, "max": maximum, "min": minimum}

# 사용 예시
sales_data = [100, 150, 200, 180, 220, 190, 160]
summary = data_summary(sales_data)
```

함수를 잘 활용하면 코드가 깔끔해지고 재사용성이 높아집니다. 데이터 분석에서는 같은 작업을 여러 데이터셋에 반복 적용할 때 특히 유용합니다.
