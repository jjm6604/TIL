# Function

## Function 함수
- 특정 작업을 수행하기 위한 **재사용 가능**한 코드 묶음
- 코드 중복 방지
- 코드의 재사용성 ↑, 가독성 ↑, 유지보수성 ↑

### Built-in Function 내장 함수
- 파이썬이 기본적으로 제공하는 함수
- import 없이 바로 사용 가능
- abs(), print(), input(), type(), str() 등


### 함수
- 함수 호출 = 함수를 실행하는 것
- 함수 구조 : INPUT ⇒ Docstring, function body ⇒ OUTPUT f(x)
    - INPUT = parameter 매개변수
    - OUTPUT = return value 반환값
- 함수 정의 : def 함수명(매개변수)
    - ex)  def make_sum(num_1, num_2)
- 함수 반환 값 : return 키워드 이후 반환할 값 명시. return문은 함수의 실행 종료하고, 결과를 반환함
    - 반환값이 없는 경우 결과는 **'None'**으로 return 됨.
    - ex)  return sum

```
    def make_sum(num_1, num_2) :
        sum = num_1 + num_2
        return sum
```

- 매개변수 parameter: **함수를 정의**할 때, 함수가 받을 값을 나타내는 변수
- 인자 argument : **함수를 호출**할 때, 실제로 전달되는 값 

### 인자
- 위치 인자
    - 함수 호출 시 인자의 위치에 따라 전달되는 인자
    - 위치 인자는 **함수 호출 시 반드시 값을 전달해야 함**

- 기본 인자 값
    - 함수 정의에서 매개변수에 기본 값을 할당하는 것
    - 함수 호출 시 **인자를 전달하지 않으면 기본값이 매개변수에 할당**됨

- 키워드 인자
    - 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자
    - 매개변수와 인자를 일치시키지 않고 특정 매개변수에 값 할당 가능
    - 인자 순서 상관 X, 인자의 이름 명시하여 전달
    - **호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함**

- 임의의 인자 목록
    - 정해지지 않은 개수의 인자를 처리하는 인자
    - 함수 정의 시 **매개변수 앞에 '*'** 붙여 사용
    - 여러 개의 인자를 **tuple**로 처리
    - ex) print()함수

- 임의의 키워드 인자 목록
    - 정해지지 않은 개수의 **키워드 인자**를 처리하는 인자
    - 함수 정의 시 **매개변수 앞에 '\**'** 붙여 사용
    - 여러 개의 인자를 **dictionary**로 처리
    
    
- ex) print(*objects, sep=' ', end='\n', file=None, flush=False)
### 함수 인자 권장 작성 순서 : 위치 ⇒ 기본 ⇒ 가변 ⇒ 키워드 ⇒ 가변 키워드


### Scope
- 함수는 코드 내부에 local scope 생성, 그 외 공간인 global scope로 구분
- global scope : 코드 어디에서든 참조할 수 있는 공간
- local scope : 함수가 만든 scope (**함수 내부에서만** 참조 가능!)
- global variable : global scope에 정의된 변수
- local variable : local scope에 정의된 변수


### 변수 수명주기
- 변수 수명주기는 **변수가 선언되는 위치 / 스코프**에 따라 결정됨
- **built-in scope** : 파이썬이 실행된 이후부터 영원히 유지
- **global scope** : 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
- **local scope** : 함수가 호출될 때 생성, 함수가 종료될 때까지 유지

- 이름 검색 규칙 (LEGB Rule)
    1. Local scope : 지역 범위(현재 작업중인 범위)
    2. Enclosed scope : 지역 범위 한 단계 위 범위
    3. Global scope : 최상단에 위치한 범위
    4. Built-in scope : 모든 것을 담고 있는 범위(정의하지 않고 사용할 수 있는 모든것)
    ![name resolution](https://core-electronics.com.au/media/wysiwyg/tutorials/Tim/Speed/first_image.png)

    ```
    # LEGB Rule 예시
    a = 1
    b = 2

    def enclosed():
        a = 10
        c = 3
        
        def local(c):
            print(a, b, c)   # 10 20 500
        
        local(500)
        print(a, b, c)     # 10 2 3

    enclosed()
    print(a, b)          # 1 2 
    ```

### global

- 변수의 스코프를 전역 범위로 지정
- 일반적으로 함수 내에서 전역 변수 수정하려는 경우에 사용
- 글로벌 키워드 선언 전에 접근 불가
- 매개 변수에 글로벌 사용 불가
- 가급적 사용하지 않는 것 권장
- 함수로 값을 바꾸고자 한다면 항상 **인자로 넘기고 함수의 반환 값을 사용**하는 것을 권장!


## 재귀 함수
- 함수 내부에서 자기 자신을 호출하는 함수
- **종료 조건 명확히 ! 반복되는 호출이 종료 조건을 향하도록 !**
- ex) 팩토리얼
```
# n!
def factorial(n)
	if n == 0 :
			return 1
	return n * factorial(n-1)
```

### map
- map(function, iterable)
    - function 함수, iterable 반복 가능한 객체
- 순회 가능한 데이터구조의 모든 요소에 함수를 적용하고, 그 결과를 map object로 반환

### zip
- zip(*iterables)
- 임의의 iterable을 모아 **tuple**을 원소로 하는 **zip object 반환**
- 두 개의 리스트를 딕셔너리로 변환 가능
```
keys = [1, 2, 3, 4]
values = ['a', 'b', 'c', 'd']
my_dict = dict(zip(keys,values))
```

### lambda 함수
- 이름 없이 정의 / 사용되는 익명 함수
- lambda 매개변수: 표현식
- 일회성으로 많이 사용

```
def addition(x, y):           # 일반적인 함수
	return x + y
result = addition(3, 5)

addition = lambda x, y: x + y # 람다 함수
result = addition(3, 5)
```
```
# map + lambda 활용
numbers = [1, 2, 3, 4, 5]

# 모든 numbers 두배로 만들기
result = map(lambda x: x * 2, numbers)
print(result)  # [2, 4, 6, 8, 10]
```

### Packing 패킹
- 여러 개의 값을 하나의 변수에 묶어서 담는 것
- 변수에 담긴 값들은 튜플 형태로 묶임
```
packed_values = 1, 2, 3, 4, 5
print(packed_values) # (1, 2, 3, 4, 5)
```
- '*'을 활용한 패킹
```
numbers = [1, 2, 3, 4, 5]
a, *b, c = numbers

print(a)  # 1
print(b)  # [2, 3, 4]
print(c)  # 5

```

### Unpacking 언패킹
- 패킹된 변수의 값을 개별적인 변수로 분리하여 할당하는 것
- 튜플/리스트 등의 객체의 요소들을 개별 변수에 할당
```
lst = [1, 2, 3]
a, b, c = lst

print(a) # 1
print(b) # 2
print(c) # 3
```
- '*'을 활용한 언패킹
    - '*'은 리스트의 요소를 언패킹함
```
#활용예시 1 2 3 으로 출력하고 싶은 경우
results = [1, 2, 3] 
print(*results)  # 언패킹
```
- ‘**’을 활용한 언패킹 (non-iterable unpacking)
    - ‘**’은 딕셔너리의 키-값 쌍을 함수의 키워드 인자로 언패킹

```
def my_function(x, y, z):
	print(x, y, z)

my_dict = {'x': 1, 'y': 2, 'z': 3}
my_function(**my_dict)  # 1 2 3
```

## 모듈
- **재사용**하기 위한 코드 조각 , 이미 만들어져 있음!
- 한 파일로 묶인 변수와 함수의 모음
- 특정한 기능을 하는 코드가 작성된 파이썬 파일(.py)
- 모듈 내 변수/함수에 접근하기 위해서는 import문 필요
    - ex) import math
    - help(math) 통해 모듈에 대한 설명 확인 가능
- module.변수명 / module.함수명 으로 접근 가능
- 주의 : 서로 다른 모듈이 같은 이름의 함수를 제공할 경우 문제 발생
    - 마지막에 import된 이름으로 대체됨
    - 모듈 내 모든 요소를 한번에 import 하는 * 표기는 권장 X
    - 모두 가져오기 때문에 메모리적으로도 비효율적
        - from math import *
- 사용자 정의 모듈 : 직접 정의한 모듈


**모듈, 함수 모두 재사용성 ↑**
**규모 : 패키지 > 모듈 > 함수**
**모두 재사용하기 위한 코드 조각**


## 파이썬 표준 라이브러리 
- 파이썬 언어와 함께 제공되는 다양한 모듈 / 패키지의 모음

    ### 패키지
- 관련된 모듈들을 하나의 디렉토리에 모아 놓은 것
- ex) from my_package.math import my_math  // form my_package.statistics import tools
1. 내부 패키지 : 설치 없이 바로 import 하여 사용
2. 외부 패키지 : pip를 사용하여 **설치** 후 import 필요
- pip : 외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템
    - 설치 : cli => **pip install 패키지명**
    - pip install requests
        ```
        import requests

        url='https://jsonplaceholder.typicode.com/todos/1'
        response = request.get(url).json() 
        ```
- 누가 만들어 놓은 모듈 편리하게 사용
- 모듈들의 이름 공간 구분하여 충돌 방지
- 모듈 효율적으로 관리/ 재사용 하도록 돕는 역할






## 참고사이트
- [python documentation](https://docs.python.org/ko/3/)
    - 자습서/라이브러리 레퍼런스 참고
- [파이썬 패키지 관리자(pip)](https://pypi.org/)