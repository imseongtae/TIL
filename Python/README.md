Python
---

## python TIL  document

## Table of Contents

  1. [Variable](#Variable)
  1. [Types](#types)
  1. [References](#references)
  1. [Objects](#objects)
  1. [Arrays](#arrays)
  1. [Destructuring](#destructuring)
  1. [Strings](#strings)
  1. [Functions](#functions)
  1. [Arrow Functions](#arrow-functions)
  1. [Classes & Constructors](#classes--constructors)


## Variable(변수)
- 메모리에 이름을 붙여넣고 값을 저장하는 것을 변수라고 한다. 
- 파이썬의 변수는 별도의 타입을 지정하지 않는다.
- 타입은 선언에 의해 결정된다.
- 변수의 이름은 스페이스를 포함하지 않음
- 변수의 이름은 특수문자를 제외한 알파벳 문자와 숫자, 그리고 언더스코어만(_)만 포함할 수 있음
- 변수의 이름은 숫자로 시작할 수 없음
- 파이썬 내부에서 사용하는 키워드를 사용할 수 없음 
	- and, del, from, not, while, as, elif, or, class, global, with
- 변수의 이름은 대문자와 소문자를 구분함

```python
price = input('가격을 입력하세요~~')
count = input('개수를 입력하세요~~!')
result = int(price) * int(count)
print(result)

```
네이밍 규칙: PEP8 스타일 가이드, 스네이크 표기법
언어를 배울 때는 그 언어의 규칙을 따라야 한다.
- 상수는 모두 대문자를 사용한다.
- 변수의 이름은 다른 사람이 알기 쉽게 작성한다.
- 클래스 이릉이나 상수 이외에는 대문자를 사용하지 않는다. 
- 클래스 이름 외에는 CamelCase를 사용하지 않는다. 
- 한 줄의 글자는 79자를 추천한다. 모니터 최대 길이를 고려함
- 하나의 import에는 모듈 하나만 한다. 

```python

first_name = 'ham'


```



## Type(Data Type)

타입
- 수치형
- 문자열
	- 따옴표로 감싸 나열해 놓은 것이다.
	- 인접한 문자열은 하나로 합쳐진다.
	- 긴 문자열은 괄호로 감싸야 한다.
- 문자열(확장열) 
	- 개행이나 탭 등 문자열 안에 담기 힘든 문자가 있다.
	- 특수한 문자는 \ 문자 뒤에 기호로 표기한다.
	- 확장열을 사용하지 않은 경우 문자열 앞에 접두사  r을 붙인다.
	- r을 맨앞에 붙여주면 확장문자열을 쓰지 않는다.
- 긴 문자열: 따옴표 3개를 연속으로 사용하면 80자가 넘어가는 긴 문자열도 처리할 수 있다.  
- Bool: True, False => 파이썬은 Bool값이 대문자로 시작한다
- 컬렉션: 여러개의 값을 모아서 저장하는 데이터 타입
	- list, tuple

```python

first_name = 'ham'
print('C:\\temp\\new.txt')
print(r'C:\temp\new.txt')
s = """강나루 건너서 밀받 길을 구름에 달 가듯이 가는 나그네
길은 외줄기 남도 삼백리 술 익는 마을마다 타는 저녁놀
구름에 달 가듯이 가는 나그네"""

a = True
b= 5
c = 7 == b

member1 = ['손오공', '저팔계', '사오정', '삼장법사']
member2 = ('손오공', '저팔계', '사오정', '삼장법사') 

member1[0] = '우마왕' # 변경 가능
member2[0] = '우마왕' # 변경 불가

```

## Operators


- 산술 연산자
- 고급 연산자 
	- 거듭제곱 **
	- 정수 나누기 //
	- 나머지(모듈연산자라고도 부름) %
- 복합 대입 연산자
	- 우변의 값이 수식을 계산하여 좌변에 대입한다.
	- 우변의 수식에 좌변의 변수가 올 수 있다.


```python
# 시험에 나올 확률이 높음

# 복합 대입 연산자
a -= 1 # good
b =- 1 # bad... 변수 b에 -1을 대입한 것과 같다.


```




