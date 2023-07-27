# 2023.07.27 (목) OOP 2

# 객체 지향 프로그래밍

Object Oriented Programming

## 상속

- 기존 클래스의 속성과 메서드 물려받아 새로운 하위 클래스 생성하는 것
- 사용 이유?
    1. **코드 재사용**
        - 상속 통해 기존 클래스 속성 / 메서드 재사용 가능
        - 새로운 클래스 작성 시 기존 클래스 기능 그대로 활용 가능, 중복된 코드 감소
    2. **계층 구조**
        - 상속 통해 클래스간 계층 구조 형성 가능
        - 부모 클래스와 자식 클래스 간의 관계를 표현하고, 더 구체적인 클래스 만들기 가능
    3. **유지 보수의 용이성 ↑**
        - 상속을 통해 기존 클래스 수정 필요한 경우, 해당 클래스만 수정하면 됨 ⇒ 유지보수성 ↑
        - 코드의 일관성 유지, 수정 범위 최소화
    

### 상속이 없는 경우 ?

- 학생 / 교수 정보를 나타내기 어려움

```python
class Person:
		def __init__(self, name, age):
				self.name = name
				self.age = age

		def talk(self):
				print(f'반갑습니다. {self.name} 입니다.')

s1 = Person('김학생', 23)
s2.talk()  # 반갑습니다. 김학생입니다.

p1 = Person('박교수', 59)
p1.talk()  # 반갑습니다. 박교수입니다.
```

- 메서드 중복 정의

```python
class Professor:
		def __init__(self, name, age, department):
				self.name = name
				self.age = age
				self.department = department

		def talk(self):    # 중복
				print(f'반갑습니다. {self.name} 입니다.')

class Student:        
		def __init__(self, name, age, department):
				self.name = name
				self.age = age
				self.gpa = gpa

		def talk(self):    # 중복
				print(f'반갑습니다. {self.name} 입니다.')
```

- 상속 활용한 계층 구조 변경

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'반갑습니다. {self.name} 입니다.')

class Professor(Person):
    def __init__(self, name, age, department):
        super().__init__(name, age)
        self.department = department

class Student(Person):
    def __init__(self, name, age, gpa):
        super().__init__(name, age)
        self.gpa = gpa

p1 = Professor('박교수', 40, '공학')
p1.talk()
s1 = Student('김학생', 22, 3.5)
s1.talk()
```

## Super()

++ 클래스간 두줄 간격 띄우기

## 다중 상속

- 두 개 이상의 클래스 상속 받는 경우
- 상속받은 모든 클래스 요소 활용 가능
- 중복된 속성 / 메서드 있는 경우 상속 순서에 의해 결정됨
    
    **다중 상속의 경우 상속을 받는 순서대로 찾아나감!**
    

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greeting(self):
    	return f'안녕, {self.name}'

class Mom(Person):
    gene = 'XX'
		
		def __init__(self, name):
				super().__init__(name)

    def swim(self):
        return '엄마가 수영'

class Dad(Person):
    gene = 'XY'

		def __init__(self, name):
				super().__init__(name)

    def walk(self):
        return '아빠가 걷기'

class FirstChild(Dad, Mom):
		def __init__(self, name):
				super().__init__(name)

    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 응애'

baby1 = FirstChild('아가')

print(baby1.cry())    # 첫째가 응애
print(baby1.swim())   # 첫째가 수영
print(baby1.walk())   # 아빠가 걷기
print(baby1.gene)     # XY

```

- 일반적으로 생성자 메서드 생략 하지 않음!
- 뒤에 상속받지만, 중복되는 상속 정보가 필요한 경우

```python
class FirstChild(Dad, Mom):
		**mom_gene = Mom.gene  # 뒤에 상속받지만 필요한 경우 명시적으로 변수 작성해 가져오기**

		def __init__(self, name):
				super().__init__(name)

    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 응애'

baby1 = FirstChild('아가')
print(baby1.mom_gene)    # XX
```

### 상속 관련 함수 / 메서드

**mro()**

- Method Resolution Order
- 해당 인스턴스의 클래스가 어떤 부모 클래스를 가지는지 확인하는 메서드
- 기존의 인스턴스 → 클래스 순으로 이름공간을 탐색하는 과정에서 상속 관계에 있으면 인스턴스 → 자식 클래스 → 부모 클래스로 확장

# Errors / Exception

### 디버깅

- 소프트웨어에서 발생하는 버그를 찾아내고 수정하는 과정
- 프로그램 오작동 원인을 식별하여 수정하는 작업
- 방법
    1. print함수 활용
    2. 개발환경이 제공하는 기능
    3. Python tutor
    4. 뇌 컴파일, 눈 디버깅

### 에러 Error

- 프로그램 실행 중 발생하는 예외 상황
- 유형

| 문법 에러
Syntax Error | 예외
Exception |
| --- | --- |
| 프로그램의 구문이 올바르지 않은 경우 발생
(오타, 괄호 및 콜론 누락 등의 문법적 오류) | 프로그램 실행 중 감지되는 에러 |

### 예외 Exception

- 프로그램 실행 중 감지되는 에러
- 내장 예외
    - 예외 상황을 나타내는 예외 클래스들
    - 파이썬에서 이미 정의, 특정 예외 상황에 대한 처리를 위해 사용
    - ZeroDivisionError / NameError / TypeError / ValueError / IndexError / KeyError / ModuleNotFoundError / ImportError / KeyboardInterrupt / IndentationError

- 예외 처리
    - try / except
    - try 문과  except 절 사용하여 예외 처리
    - try 블록 : 예외가 발생할 수 있는 코드
    - except 블록 : 예외 발생 시 처리할 코드
    - 예외 발생 시 프로그램 흐름은 try 블록 빠져나와 해당 예외에 대응하는 except 블록으로 이동
    
    ```python
    try:
    		# 예외가 발생할 수 있는 코드
    
    except 예외:
    		# 예외 처리 코드
    ```
    
    ```python
    try:
        num = int(input('100으로 나눌 값을 입력하세요 :'))
        print(100 / num)
    
    except ValueError:
        print('숫자가 아닙니다.')
    
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    
    except:
        print('Error 발생')
    ```
    
    - 내장 예외 클래스는 **상속 계층구조**를 가짐 !
        
        ⇒ except 절로 분기 시 **반드시 하위 클래스를 먼저 확인 할 수 있도록 작성**
        
    - [예외 계층 구조](https://docs.python.org/ko/3/library/exceptions.html#exception-hierarchy)
    
    ![Untitled](2023%2007%2027%20(%E1%84%86%E1%85%A9%E1%86%A8)%20OOP%202%20f044692286324013a78abc5a99ddd15c/Untitled.png)
    

### 예외처리 방법

### **1. EAFP**

- Easier to Ask for Forgiveness than Permission
- 예외처리 중심으로 코드를 작성하는 접근 방식(try-except)

### 2. LBYL

- Look Before You Leap
- 값 검사 중심으로 코드를 작성하는 접근 방식 (if-else)

```python
# EAFP (파이썬 권장 방식/ but 이유는 딱히 X)
try:
		result = my_dict['key']
		print(result)
except KeyError:
		print('Key가 존재하지 않습니다.')

# LBYL
if 'key' in my_dict:
		result = my_dict['key']
		print(result)
else:
		print('Key가 존재하지 않습니다.')
```

| EAFP | LBYL |
| --- | --- |
| 일단 실행하고 예외 처리 | 실행하기 전에 조건을 검사 |
| 코드를 실행하고 예외가 발생하면 예외 처리를 수행 | 코드 실행 전 조건문 등을 사용하여 예외 상황을 미리 검사하고 예외 상황을 피하는 방식 |
| 코드에서 예외가 발생할 수 있는 부분을 미리 예측하여 대비하는 것이 아니라, 예외가 발생한 후 예외를 처리 | 코드가 좀 더 예측 가능한 동작을 하지만, 코드가 더 길고 복잡해질 수 있음 |
| 예외 상황을 예측하기 어려운 경우에 유용 | 예외 상황을 미리 방지하고 싶을 때 유용 |

### as

- as 키워드 활용하여 에러 메시지 except 블록에서 사용 가능

```python
my_list = []
try:
		number = my_list[1]
except IndexError as error:
		print(f'{error}가 발생했습니다.')

# list index out of range가 발생했습니다.
```