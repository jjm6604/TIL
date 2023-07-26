# 2023.07.26 (수) OOP 1

# 객체 지향 프로그래밍

**Object Oriented Programming**

- **절차 지향 프로그래밍(Procedural Programming)**
    - 프로그램을 **‘데이터’** 와 **‘절차’** 로 구성하는 방식의 프로그래밍 패러다임
    - ‘데이터’, ‘절차’(함수) 분리해서 처리 , 함수 호출의 흐름이 중요!
    - 코드의 순차적인 흐름과 함수 호출에 의해 프로그램이 진행
    - 데이터를 다시 재사용하기 보다는 처음~끝까지 실행되는 결과물이 중요한 방식
    - but, 하드웨어 발전 → 컴퓨터 계산용량 문제 / 복잡성 급격히 증가 = 소프트웨어 위기

## 객체 지향 프로그래밍

- 데이터와 해당 데이터를 조작하는 메서드를 **하나의 객체로 묶어 관리**하는 방식의 프로그래밍 패러다임
    - 메서드 ⇒ 객체에 속한 함수
- 절차 지향 기반으로 보완하여 고안된 새로운 패러다임

| 절차 지향 | 객체 지향 |
| --- | --- |
| 데이터와 해당 데이터를 처리하는 함수(절차)가 분리 | 데이터와 해당 데이터를 처리하는 메서드(메시지)를 하나의 객체(클래스)로 묶음 |
| 함수 호출 흐름이 중요! | 객체 간 상호작용과 메시지 전달 중요! |

## 클래스 Class

- 파이썬에서 타입을 표현하는 방법
- 객체를 생성하기 위한 **설계도**
- 데이터와 기능을 함께 묶는 방법 제공

### **객체 Object**

- 클래스에서 정의한 것을 토대로 메모리에 할당된 것
- ‘**속성**’과 ‘**행동**’ 으로 구성된 모든 것
- 속성 = 변수      //     행동 = 메서드
- 클래스로 만든 객체 ⇒ **인스턴스**

<aside>
💡 **가수 (클래스)**
아이유는 객체다(O)
아이유는 인스턴스다 (X)
아이유는 가수의 인스턴스다(O)

</aside>

### 클래스와 객체

- 클래스로 만든 객체 = **인스턴스**
- 변수 name의 타입은 str 클래스
- 변수 name은 **str 클래스의 인스턴스**
- 우리가 사용해왔던 데이터 타입 = 모두 클래스

```python
name = 'Alice'
print(type(name))  # <class 'str'>
```

```python
'', 'hello', '파이썬'
# 문자열 타입(클래스)의 객체(인스턴스)

[1, 2, 3], [1], [], ['hi']
# 리스트 타입(클래스)의 객체(인스턴스)
```

### 인스턴스와 메서드

- 문자열.대문자로()
- 객체.행동()
- 인스턴스.메서드()
    
    ex) “hello”.upper()
    

### 객체의 특징

- 타입(type) : 어떤 연산자와 조작이 가능한가?
- 속성(attribute) : 어떤 상태(데이터)를 가지는가?
- 조작법(method) : 어떤 행위(함수)를 할 수 있는가?

```python
# 클래스 정의
class Person:
    # 속성(변수)
    blood_color = 'red'
    # 메서드
    def __init__(self, name):
        self.name = name

    def singing(self):
        return f'{self.name}가 노래합니다.'
    

# 인스턴스 생성
singer1 = Person('iu')
singer2 = Person('BTS')

# 메서드 호출
print(singer1.singing())
print(singer2.singing())
print(singer1.blood_color)
print(singer2.blood_color)

singer1.name = 'gggg'
print(singer1.singing())
```

### 인스턴스와 클래스 간 이름 공간

- 클래스 정의 하면 클래스와 해당하는 이름 공간 생성
- 인스턴스 만들면 인스턴스 객체 생성되고 **독립적인 이름 공간 생성**
- 인스턴스에서 특정 속성에 접근하면 인스턴스 → 클래스 순으로 탐색

```python
# 클래스 정의
class Person:
    count = 0

    def __init__(self, name):
        self.name = name
        Person.count += 1

person1 = Person('iu')
person2 = Person('BTS')
# 인스턴스 만들 때마다 count += 1
print(Person.count)     # 2
```

- 클래스 변수 변경할 때는 항상 **클래스.클래스변수** 형식으로 변경

```python
class Circle():
    pi = 3.14

    def __init__(self, r):
        self.r = r

c1 = Circle(5)
c2 = Circle(10)

print(Circle.pi)    # 3.14
print(c1.pi)        # 3.14
print(c2.pi)        # 3.14

Circle.pi = 5

print(Circle.pi)    # 5
print(c1.pi)        # 5
print(c2.pi)        # 5

c1.pi = 5

print(Circle.pi)    # 3.14
print(c1.pi)        # 5
print(c2.pi)        # 3.14
```

### 메서드

1. **인스턴스 메서드**
- 클래스로부터 생성된 각 인스턴스에서 호출할 수 있는 메서드
- 인스턴스의 상태 조작하거나 동작을 수행
- 구조
    - 반드시 **첫 번째 매개변수로 인스턴스 자신(self)을 전달받음**
    - 무조건 ‘self’
    
    ```python
    class MyClass:
    		def instance_method(self, arg1, ...):
    				pass
    ```
    
    - self 동작 원리
        - str 클래스가 upper 메서드를 호출했고, 그 첫번째 인자로 문자열 인스턴스가 들어간 것
            
            **⇒ 인스턴스 메서드의 첫번재 매개변수가 반드시 인스턴스 자기 자신(self)인 이유!**
            
        - ‘hello’.upper() 는 str.upper(’hello’)를 객체지향 방식의 메서드로 호출하는 표현(단축형 호출)
        - ‘hello’라는 문자열 객체가 단순히 어딘가의 함수로 들어가는 인자가 아닌 객체 스스로 메서드를 호출하여 코드를 동작하는 객체 지향적 표현
    
    ```python
    # 인스턴스.메서드()    
    'abc'.upper()
    
    # 클래스.메서드(인스턴스 자기자신)    // 파이썬 내부 동작은 이렇게 이루어짐
    str.upper('abc')
    
    # 둘 다 같은 코드임!
    
    ```
    
- 생성자 메서드 constructor method
    - 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
    - 인스턴스 변수들의 초기값을 설정
    
    ```python
    def __init__(self):
    		pass
    ```
    
1. **클래스 메서드**
- 클래스가 호출하는 메서드
- 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행
- **@classmethod** 데코레이터 사용하여 정의
- 호출 시 첫번째 인자로 호출하는 **클래스(cls)가 전달**됨

```python
class MyClass:
		@classmethod
		def class_method(cls, arg1, ...):
				pass
```

```python
class Person:
		count = 0

		def __init__(self, name):
				self.name = name
				Person.count += 1

		@classmethod
		def number_of_population(cls):
				print(f'인구수는 {cls.count}입니다.')

person1 = Person('iu')
person2 = Person('BTS')

Person.number_of_population() # 인구수는 2입니다.

```

1. **스태틱**(**정적) 메서드**
- 클래스와 인스턴스 상관없이 독립적으로 동작하는 메서드
- 주로 클래스와 관련이 있지만 인스턴스와 상호작용이 필요하지 않은 경우에 사용
- 구조
    - @staticmethod 데코레이터 사용하여 정의
    - 호출 시 필수적으로 작성해야 할 매개변수 X
    - 객체 상태나 클래스 상태 수정 X, 단지 **기능(행동)만을 위한 메서드**로 사용
    
    ```python
    class MyClass:
    	
    		@staticmethod
    		def static_method(arg1, ...):
    				pass
    
    ```
    
    ```python
    class StringUtils:
    		@staticmethod
    		def reverse_string(string):
    				return string[::-1]
    
    		@staticmethod
    		def capitalize_string(string):
    				return string.capitalize()
    
    text = 'hello, world'
    
    reversed_text = StringUtils.reverse_string(text)
    print(reversed_text)     # dlrow ,olleh
    
    capitalized_text = StringUtils.capitalize_string(text)
    print(capitalized_text)  # Hello, World
    ```
    

### 인스턴스 메서드

- 인스턴스 상태를 변경하거나, 해당 인스턴스의 특정 동작 수행
- 첫 번째 인자로 !! self !!

### 클래스 메서드

- 인스턴스 상태에 의존하지 않는 기능 정의
- 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행
- 첫 번째 인자로 !! cls !!
- @classmethod

### 스태틱 메서드

- 클래스 및 인스턴스와 관련이 없는 일반적인 기능을 수행
- @staticmethod

<aside>
💡 **역할**

**클래스가 사용해야 할 것**

- 클래스 메서드
- 스태틱 메서드

**인스턴스가 사용해야 할 것**

- 인스턴스 메서드
</aside>

### 클래스

- 클래스 ⇒ 모든 메서드 호출 가능
    - but !!  클래스는 **클래스 메서드**와 **스태틱 메서드**만 사용하도록 !

- 인스턴스 ⇒ 모든 메서드 호출 가능
    - but !! 인스턴스는 **인스턴스 메서드**만 사용하도록 !

### 할 수 있다 ≠ 써도 된다

- 각자의 메서드는 OOP 패러다임에 따라 명확한 목적에 따라 설계된 것이기 때문에 클래스와 인스턴스 각각 올바른 메서드만 사용하도록 해야함

### 매직 메서드

- 특별한 인스턴스 메서드
- 특정 상황에 자동으로 호출되는 메서드

```python
class Circle:
		def __init__(self, r):
				self.r = r

		def area(self):
				return 3.14 * self.r * self.r
		
		def __str__(self):
				return f'[원] radius: {self.r}'
```

### 데코레이터

- 다른 함수의 코드를 유지한 채로 수정하거나 확장하기 위해 사용되는 함수

<aside>

- **절차 지향과 객체 지향은 대비되는 개념이 아님!**
- 객체 지향은 기존 절차 지향을 기반으로 두고 보완하기 위해 객체라는 개념을 도입해 **상속, 코드 재사용성, 유지보수성** 등의 이점을 가지는 패러다임
</aside>