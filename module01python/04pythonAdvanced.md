# 객체/클래스

## 1. 객체지향 프로그래밍 개념

### 객체(Object)와 클래스(Class)

- **클래스**: 객체를 만들기 위한 설계도, 틀
- **객체**: 클래스로부터 생성된 실제 인스턴스
- **속성(Attribute)**: 객체가 가지는 데이터
- **메서드(Method)**: 객체가 수행할 수 있는 동작

```python
# 예시: 자동차 클래스와 객체
# 클래스 = 자동차 설계도
# 객체 = 실제 자동차 (소나타, 아반떼 등)
```

## 2. 클래스 정의와 객체 생성

### 기본 클래스 정의

```python
class Person:
    # 클래스 변수 (모든 인스턴스가 공유)
    species = "Homo sapiens"
    
    # 생성자 메서드
    def __init__(self, name, age):
        # 인스턴스 변수 (각 객체마다 고유)
        self.name = name
        self.age = age
    
    # 인스턴스 메서드
    def introduce(self):
        return f"안녕하세요, 저는 {self.name}이고 {self.age}살입니다."
    
    def birthday(self):
        self.age += 1
        print(f"{self.name}의 나이가 {self.age}살이 되었습니다!")
```

### 객체 생성과 사용

```python
# 객체 생성
person1 = Person("김철수", 25)
person2 = Person("이영희", 30)

# 속성 접근
print(person1.name)     # "김철수"
print(person1.age)      # 25
print(person1.species)  # "Homo sapiens"

# 메서드 호출
print(person1.introduce())  # "안녕하세요, 저는 김철수이고 25살입니다."
person1.birthday()          # "김철수의 나이가 26살이 되었습니다!"
```

## 3. 클래스의 구성요소

### 생성자(**init**)

```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand      # 인스턴스 변수
        self.model = model
        self.year = year
        self.mileage = 0        # 기본값 설정
    
# 사용
my_car = Car("현대", "소나타", 2023)
```

### 인스턴스 메서드

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
    
    def deposit(self, amount):
        """입금 메서드"""
        if amount > 0:
            self.balance += amount
            print(f"{amount}원이 입금되었습니다. 잔액: {self.balance}원")
    
    def withdraw(self, amount):
        """출금 메서드"""
        if amount > self.balance:
            print("잔액이 부족합니다.")
        else:
            self.balance -= amount
            print(f"{amount}원이 출금되었습니다. 잔액: {self.balance}원")
    
    def get_balance(self):
        """잔액 조회 메서드"""
        return self.balance

# 사용 예시
account = BankAccount("김철수", 10000)
account.deposit(5000)   # 15000원
account.withdraw(3000)  # 12000원
print(account.get_balance())  # 12000
```

### 클래스 변수 vs 인스턴스 변수

```python
class Student:
    # 클래스 변수 (모든 인스턴스가 공유)
    school = "파이썬 고등학교"
    student_count = 0
    
    def __init__(self, name, grade):
        # 인스턴스 변수 (각 객체마다 고유)
        self.name = name
        self.grade = grade
        Student.student_count += 1  # 클래스 변수 수정
    
    def study(self, subject):
        print(f"{self.name}이(가) {subject}를 공부합니다.")

# 사용
student1 = Student("김철수", 2)
student2 = Student("이영희", 3)

print(Student.school)         # "파이썬 고등학교"
print(Student.student_count)  # 2
print(student1.school)        # "파이썬 고등학교"
print(student1.name)          # "김철수"
```

## 4. 특수 메서드 (Magic Methods)

### __str__와 **repr**

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages
    
    def __str__(self):
        """사용자가 읽기 쉬운 문자열 표현"""
        return f"'{self.title}' by {self.author}"
    
    def __repr__(self):
        """개발자용 문자열 표현"""
        return f"Book('{self.title}', '{self.author}', {self.pages})"
    
    def __len__(self):
        """len() 함수 사용 시 반환값"""
        return self.pages

# 사용
book = Book("파이썬 입문", "김코딩", 300)
print(str(book))    # "'파이썬 입문' by 김코딩"
print(repr(book))   # "Book('파이썬 입문', '김코딩', 300)"
print(len(book))    # 300
```

### 비교 연산자

```python
class Score:
    def __init__(self, value):
        self.value = value
    
    def __eq__(self, other):
        """== 연산자"""
        return self.value == other.value
    
    def __lt__(self, other):
        """< 연산자"""
        return self.value < other.value
    
    def __str__(self):
        return f"점수: {self.value}"

# 사용
score1 = Score(85)
score2 = Score(90)

print(score1 == score2)  # False
print(score1 < score2)   # True
```

## 5. 실제 활용 예제

### 계산기 클래스

```python
class Calculator:
    def __init__(self):
        self.result = 0
    
    def add(self, num):
        self.result += num
        return self
    
    def subtract(self, num):
        self.result -= num
        return self
    
    def multiply(self, num):
        self.result *= num
        return self
    
    def divide(self, num):
        if num != 0:
            self.result /= num
        else:
            print("0으로 나눌 수 없습니다.")
        return self
    
    def get_result(self):
        return self.result
    
    def clear(self):
        self.result = 0
        return self

# 메서드 체이닝 사용
calc = Calculator()
result = calc.add(10).multiply(2).subtract(5).get_result()
print(result)  # 15.0
```

### 게임 캐릭터 클래스

```python
class GameCharacter:
    def __init__(self, name, hp, attack):
        self.name = name
        self.hp = hp
        self.max_hp = hp
        self.attack = attack
        self.level = 1
    
    def attack_enemy(self, enemy):
        print(f"{self.name}이(가) {enemy.name}을(를) 공격합니다!")
        enemy.take_damage(self.attack)
    
    def take_damage(self, damage):
        self.hp -= damage
        print(f"{self.name}이(가) {damage}의 데미지를 받았습니다. (HP: {self.hp})")
        if self.hp <= 0:
            print(f"{self.name}이(가) 쓰러졌습니다!")
    
    def heal(self, amount):
        self.hp = min(self.hp + amount, self.max_hp)
        print(f"{self.name}이(가) {amount}만큼 회복했습니다. (HP: {self.hp})")
    
    def is_alive(self):
        return self.hp > 0

# 사용
warrior = GameCharacter("전사", 100, 25)
mage = GameCharacter("마법사", 80, 30)

warrior.attack_enemy(mage)  # 전사가 마법사 공격
mage.attack_enemy(warrior)  # 마법사가 전사 공격
```

## 6. 객체지향의 장점

### 코드 재사용성

```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        pass

class Dog(Animal):  # 상속 (다음 단계에서 자세히 다룰 예정)
    def speak(self):
        return f"{self.name}이(가) 멍멍!"

class Cat(Animal):
    def speak(self):
        return f"{self.name}이(가) 야옹!"
```

### 데이터 캡슐화

```python
class Temperature:
    def __init__(self, celsius=0):
        self._celsius = celsius  # private 변수 (관례상 _로 시작)
    
    def get_celsius(self):
        return self._celsius
    
    def set_celsius(self, value):
        if value < -273.15:
            raise ValueError("절대영도 이하의 온도는 불가능합니다.")
        self._celsius = value
    
    def get_fahrenheit(self):
        return (self._celsius * 9/5) + 32
```



# Python의 "모든 것은 객체Everything is an object" 철학

### 기본 데이터 타입도 객체

```python
# 정수도 객체입니다
num = 42
print(type(num))        # <class 'int'>
print(dir(num))         # int 클래스의 모든 메서드 확인

# 정수 객체의 메서드 사용
print(num.bit_length()) # 42를 이진수로 표현할 때 필요한 비트 수
print(num.__add__(8))   # 42 + 8 = 50

# 문자열도 객체입니다
text = "Hello World"
print(type(text))       # <class 'str'>
print(text.upper())     # 문자열 객체의 메서드
print(text.count('l'))  # 'l' 문자의 개수
```

### 데이터 타입별 클래스 확인

```python
# 모든 기본 타입이 클래스로 구현됨
print(type(42))         # <class 'int'>
print(type(3.14))       # <class 'float'>
print(type("hello"))    # <class 'str'>
print(type(True))       # <class 'bool'>
print(type([1,2,3]))    # <class 'list'>
print(type({1,2,3}))    # <class 'set'>
print(type({'a':1}))    # <class 'dict'>

# 심지어 함수도 객체입니다
def my_function():
    pass

print(type(my_function))  # <class 'function'>
```

## 객체로서의 데이터 타입 특성

### 1. 속성과 메서드를 가짐

```python
# 리스트 객체의 메서드들
numbers = [1, 2, 3]
print(dir(numbers))  # 리스트가 가진 모든 메서드 확인

# 실제 사용
numbers.append(4)      # 메서드 호출
numbers.extend([5,6])  # 메서드 호출
print(numbers.count(2)) # 메서드 호출

# 문자열 객체의 메서드들
text = "python programming"
print(text.capitalize())  # "Python programming"
print(text.replace('python', 'Python'))
print(text.split())       # ['python', 'programming']
```

### 2. 동적으로 속성 추가 가능 (일부 타입)

```python
# 함수도 객체이므로 속성 추가 가능
def greet():
    return "Hello!"

greet.language = "Korean"  # 함수 객체에 속성 추가
greet.version = 1.0

print(greet.language)  # "Korean"
print(greet())         # "Hello!"
```

### 3. 객체 ID와 참조

```python
# 모든 객체는 고유한 ID를 가짐
a = 100
b = 100
print(id(a))  # 객체의 메모리 주소
print(id(b))  # 작은 정수는 캐싱되어 같은 ID

# 리스트는 다른 객체
list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(id(list1))  # 다른 ID
print(id(list2))  # 다른 ID
print(list1 is list2)  # False (다른 객체)
```

## 내부 구조 살펴보기

### 클래스로서의 int

```python
# int는 실제로 클래스입니다
print(int.__doc__)      # int 클래스의 설명
print(int.__name__)     # 'int'

# int 생성자 사용
num1 = int(42)          # int() 생성자 호출
num2 = int("123")       # 문자열을 정수로 변환
num3 = int(3.14)        # 실수를 정수로 변환

print(num1, num2, num3) # 42 123 3
```

### 클래스로서의 str

```python
# str 클래스의 다양한 생성 방법
text1 = str()           # 빈 문자열
text2 = str(123)        # 숫자를 문자열로
text3 = str([1,2,3])    # 리스트를 문자열로

print(repr(text1))      # ''
print(text2)            # '123'
print(text3)            # '[1, 2, 3]'
```

## 실제 예제: 데이터 타입의 객체적 특성 활용

### 문자열 메서드 체이닝

```python
text = "  python programming is fun  "
result = text.strip().upper().replace('PYTHON', 'Python').split()
print(result)  # ['Python', 'PROGRAMMING', 'IS', 'FUN']
```

### 리스트 메서드와 속성

```python
numbers = [3, 1, 4, 1, 5, 9]
print(f"리스트 길이: {len(numbers)}")
print(f"최댓값: {max(numbers)}")
print(f"최솟값: {min(numbers)}")

# 리스트 객체의 메서드들
numbers.sort()          # 정렬
numbers.reverse()       # 역순
print(numbers)          # [9, 5, 4, 3, 1, 1]
```

### 딕셔너리 객체의 활용

```python
data = {'name': '김철수', 'age': 25}

# 딕셔너리 객체의 메서드들
print(data.keys())      # dict_keys(['name', 'age'])
print(data.values())    # dict_values(['김철수', 25])
print(data.items())     # dict_items([('name', '김철수'), ('age', 25)])

# 메서드 체이닝
result = data.get('name', 'Unknown').upper()
print(result)           # '김철수'
```

## 사용자 정의 클래스와의 비교

```python
# 내장 타입과 같은 방식으로 동작하는 사용자 정의 클래스
class MyNumber:
    def __init__(self, value):
        self.value = value
    
    def __add__(self, other):
        return MyNumber(self.value + other.value)
    
    def __str__(self):
        return str(self.value)

# 내장 타입처럼 사용
num1 = MyNumber(10)
num2 = MyNumber(20)
result = num1 + num2    # __add__ 메서드 호출
print(result)           # 30
```


#  Python은 하이브리드 언어

## Python은 Interpreter 언어인가?

**정확히는 "하이브리드(Hybrid)" 언어입니다.**

Python은 순수한 interpreter 언어가 아닙니다. Python은 하이브리드 언어의 예시 중 하나로, C#, Java, JavaScript와 함께 분류됩니다.

### Python의 실행 과정

```python
# 1단계: 소스 코드 (.py)
print("Hello, World!")

# 2단계: 바이트코드로 컴파일 (.pyc 파일 생성)
# Python 인터프리터가 자동으로 수행

# 3단계: Python Virtual Machine(PVM)에서 바이트코드 해석 및 실행
```

## 프로그래밍 언어의 3가지 주요 분류

### 1. 컴파일드(Compiled) 언어

#### 특징

- 소스 코드를 기계어로 미리 번역
- 실행 파일(.exe 등) 생성
- 실행 속도가 빠름
- 플랫폼 종속적

#### 예시 언어들

```c
// C 언어 예제
#include <stdio.h>
int main() {
    printf("Hello, World!\n");
    return 0;
}
// gcc로 컴파일 → 실행 파일 생성
```

**주요 언어**: C, C++, Rust, Go, Fortran

### 2. 인터프리터드(Interpreted) 언어

#### 특징

- 소스 코드를 사용자 기계에 그대로 복사하여 전달하고, 기계가 프로그램을 실행할 때 인터프리터가 소스 코드를 한 줄씩 즉시 해석합니다.
- 별도 파일을 생성하지 않음
- 개발과 테스트가 빠름
- 실행 속도는 상대적으로 느림

#### 예시 언어들

```javascript
// JavaScript (브라우저에서 즉시 실행)
console.log("Hello, World!");
```

```bash
# Bash 스크립트
echo "Hello, World!"
```

**주요 언어**: JavaScript(브라우저), PHP, Ruby, Perl, Shell scripts

### 3. 하이브리드(Hybrid) 언어

#### 특징

- 하이브리드 번역은 컴파일러와 인터프리터를 모두 사용합니다. 고수준 소스 코드를 바이트코드와 같은 저수준 형태로 컴파일한 다음, 인터프리터를 사용하여 실행합니다.
- 컴파일과 해석의 장점을 결합
- 플랫폼 독립성과 최적화를 모두 제공

#### Python의 경우

```python
# 1. 소스 코드 (hello.py)
def greet(name):
    return f"Hello, {name}!"

print(greet("World"))

# 2. 바이트코드로 컴파일 (__pycache__/hello.cpython-311.pyc)
# 3. Python Virtual Machine에서 실행
```

#### Java의 경우

```java
// 1. 소스 코드 (Hello.java)
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}

// 2. javac로 바이트코드 컴파일 (Hello.class)
// 3. JVM에서 실행
```

**주요 언어**: Python, Java, C#, JavaScript(Node.js)

## 언어별 분류 표

|분류|언어 예시|실행 방식|장점|단점|
|---|---|---|---|---|
|**컴파일드**|C, C++, Rust, Go|소스코드 → 기계어|빠른 실행속도, 최적화|컴파일 시간, 플랫폼 종속|
|**인터프리터드**|JavaScript, PHP, Ruby|소스코드 → 즉시 실행|빠른 개발, 플랫폼 독립|느린 실행속도|
|**하이브리드**|Python, Java, C#|소스코드 → 중간코드 → 실행|양쪽 장점 결합|복잡한 구조|

## 실제 언어 분류의 복잡성

### 현실적인 관점

거의 모든 언어는 어느 정도 두 접근 방식의 하이브리드이며, 언어 자체가 아닌 언어 구현체가 컴파일되거나 해석되는 것입니다.

### 언어별 다양한 구현체

```python
# Python의 다양한 구현체
# CPython (표준): 바이트코드 → 인터프리터
# PyPy: JIT 컴파일러 사용
# Cython: C로 컴파일
# Jython: Java 바이트코드로 컴파일
```

### JavaScript의 진화

```javascript
// 과거: 순수 인터프리터
// 현재: V8 엔진 (JIT 컴파일러)
// - 자주 사용되는 코드를 기계어로 컴파일
// - 성능 최적화
```

## 최신 트렌드: JIT 컴파일

### Just-In-Time 컴파일러

JIT 컴파일은 중간 표현을 런타임에 네이티브 기계 코드로 컴파일하는 기술입니다.

```python
# PyPy (Python JIT 구현체)
# 자주 실행되는 코드를 실시간으로 기계어로 컴파일
# → 인터프리터보다 훨씬 빠른 성능
```

## 정리

1. **Python은 하이브리드 언어**입니다
2. **3가지 주요 분류**: 컴파일드, 인터프리터드, 하이브리드
3. **현실적으로는 대부분 하이브리드** 형태
4. **성능과 편의성의 균형**을 맞추는 방향으로 발전

언어 분류보다는 "어떤 문제를 해결하는데 가장 적합한가?"를 고려하는 것이 더 실용적입니다. Python은 데이터 분석, 웹 개발, AI 등에서 뛰어난 생산성을 제공하는 하이브리드 언어로 널리 사용되고 있습니다!
