# 🌟list

## ✏️list
- **여러 개**의 값을 **순서대로** 저장하는, **변경 가능한(mutable)** 시퀀스 자료형
- 대괄호 [ ]안에 값들을 쉼표(,)로 구분하여 만듦
- 숫자, 문자열, 다른 리스트까지 **모든 종류 데이터 담을 수 있음**
  > 다른 언어는 같은 데이터 타입의 복수 데이터만 가능
- 값을 추가, 수정, 삭제하는 등 자유롭게 변경 가능

## ✏️시퀀스로서의 리스트
- 리스트는 시퀀스이므로 인덱싱, 슬라이싱, 길이 확인, 반복 등 공통 기능 모두 사용 가능

## ✏️중첩 리스트 (Nested List)
- 다른 리스트를 값으로 가진 리스트
- 중첩(Nested) : 어떤 자료 구조 안에 같은 종류의 자료 구조가 포함된 형태
- 중첩 리스트 접근
  - 인덱스 연달아 사용하여 안쪽 리스트 값에 접근 가능
  ```python
    my_list = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
    print(len(my_list)) # 5
    print(my_list[4][-1]) # !!!
    print(my_list[-1][1][0]) # w
  ```

## ✏️리스트의 가변성
- 한번 생성된 리스트는 그 내용을 자유롭게 수정, 추가, 삭제 가능
- 불변성과 정반대되는 매우 중요한 특징
```python
    #1. 인덱싱으로 값 수정
    my_list = [1, 2, 3, 4, 5]
    my_list[1] = 'two'
    print(my_list) # [1, 'two', 3, 4, 5]

    #2. 슬라이싱으로 여러 값 한번에 바꾸기
    my_list = [1, 2, 3, 4, 5]
    my_list[2:4] = ['three', 'four']
    print(my_list) # [1, 2, 'three', 'four', 5]
```


# tuple

## ✏️tuple
- 여러 개의 값을 순서대로 저장하는 **변경 불가능한** 시퀀스 자료형
- 소괄호 ( )안에 값들을 쉼표(,)로 구분하여 만듦
- 모든 종류 데이터 담을 수 있음
- 리스트와 거의 비슷, 한번 만들어지면 절대 수정할 수 없다는 결정적 차이
- 소괄호 없이도 만들 수 있음
- 단일 요소 튜플 만들 때 *반드시 Trailing comma(후행 쉼표) 사용*
```python
    my_tuple_2 = (1,)
    my_tuple_4 = 1, 'hello', 3.14, True
```

## ✏️시퀀스로서의 튜플
- 튜플 역시 시퀀스이므로 인덱싱, 슬라이싱, 길이 확인, 반복 등 공통 기능 모두 사용 가능


## ✏️튜플의 불변성
- 한번 생성된 튜플은 그 내용 절대 수정, 추가, 삭제 불가
- 튜플이 불변 자료형인 이유
  - 튜플의 불변 특성 사용하여 **내부 동작**(python이 내부적으로 사용)과 안전한 데이터 전달에 사용됨
  - 다중 할당, 값 교환, 함수 다중 반환 값 등
  - 튜플은 데이터의 안정성과 무결성 보장
  >  내부동작이기 때문에 개발자가 직접적으로 활용하지는 않음


# range

## ✏️range
- **연속된 정수 시퀀스**를 생성하는 **변경 불가능한(immutable)** 자료형
- 주로 반복문과 함께 사용, 특정 횟수만큼 코드 반복 실행 때 유용
- 실제로 모든 숫자 메모리에 저장하는 대신 시작값, 끝값, 간격이라는 '규칙'만 기억 -> 메모리 효율적으로 사용
  > ex. 1 생성 후, 2 생성할 때 1 삭제. 3 생성할 때 2 삭제. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*맞는지 확인*
- range( )는 3개까지의 매개변수(인자)를 가질 수 있음
    > 매개변수 : 함수 정의할 때, 함수가 받을 값을 나타내는 변수
    >
    > 인자 : 함수 호출할 때, 실제로 전달되는 값
 
## ✏️range 기본 구문
- `range(start, stop, step)`
- 매개변수별 특징
  - range(stop)
    - 매개변수가 하나면 stop으로 인식
    - start = 0, step = 1이 기본값
    - range(5) -> 0, 1, 2, 3, 4
  - range(start, stop)
    - 매개변수 두 개면 start와 stop으로 인식
    - step = 1이 기본값
    - range(2, 5) -> 2, 3, 4
  - range(start, stop, step)
    - 모든 매개변수 직접 지정
    - range(2, 10, 2) -> 2, 4, 6, 8
- range는 list로 형변환 시 내부 값 확인 가능
```python
    my_range_1 = range(5)
    print(my_range_1) # range(0, 5)
    print(list(my_range_1)) # [0, 1, 2, 3, 4]
```

## ✏️range의 규칙
1. 값의 범위 규칙
    - stop 값은 생성되는 시퀀스에 포함 X
    - range(1, 5)는 1부터 5 '전'까지 숫자이므로 1, 2, 3, 4
2. 증가/감소 값(step) 규칙
    - step 값은 숫자 시퀀스의 간격과 방향 결정
      1. step 양수일 때 (기본값 : 1)
         - 숫자가 start부터 stop을 향해 증가
         - range(1, 10, 2) -> 1, 3, 5, 7, 9
      2. step 음수일 때
         - 숫자가 start부터 stop을 향해 감소
         - start 값은 stop 값보다 반드시 커야 함
         - range(10, 1, -2) -> 10, 8, 6, 4, 2
-  range 활용 예시
   -  주로 반복문과 함께 활용 예정
     ```python
        for i in range(1, 10):
     ```
 
# 🌟dict

## ✏️딕셔너리 (dict)
- **key-value 쌍**으로 이루어진 **순서와 중복이 없는** **변경 가능한** 자료형
- 중괄호 { }안에 값들이 쉼표(,)로 구분되어 있음
- 값 1개는 키와 값이 쌍으로 이루어져 있음
- Key(키) : 값을 식별하기 위한 고유한 '이름표' (중복 불가)
- Value(값) : 키에 해당하는 실제 데이터
- 🌟각 값에는 순서가 없음
  - 파이썬 3.7 이상에서는 입력한 순서는 출력 시 그대로 유지
  - but 딕셔너리 핵심은 **순서가 없는 자료형**이라는 점, **Key를 통한 접근**이라는 점 기억!
- 딕셔너리 안에 딕셔너리 중첩할 수 있음
  ```python
    dict1 = {1:'a', 2:'b', 'fruit': ['apple', 'banana'], 'animal': {1:['man', 'woman'], 2:['dog', 'cat']}}

    print(dict1['animal'])              # {1:['man', 'woman'], 2:['dog', 'cat']}
    print(dict1['animal'][1])           # ['man', 'woman']
    print(dict1['animal'][1][0])        # man
    print(dict1['animal'][1][0][1])     # a
  ```

## ✏️딕셔너리 규칙
- Key의 규칙
  - 고유해야 함
    - key는 중복 X
  - 변경 불가능한 자료형만 사용 가능
    - O : str, int, float, ruple
    - X : list, dict
- Value의 규칙
  - 어떤 자료형이든 자유롭게 사용 가능

## ✏️딕셔너리 값 접근
- 딕셔너리 값 접근 방법
  - Key 사용하여 해당 Value 꺼내 올 수 있음
  - Key에 접근 시 대괄호 [ ] 사용
  - 존재하지 않는 Key 접근하면 KeyError 발생, 프로그램 멈춤
  - 사전처럼, 딕셔너리는 key를 통해 value에 빠르게 접근
- 딕셔너리 값 추가 및 변경
```python
    my_dict = {'apple': 12, 'list': [1, 2, 3]}
    # 추가
    my_dict['banana'] = 50
    print(my_dict) # {'apple': 12, 'list': [1, 2, 3], 'banana': 50}
    # 변경
    my_dict['apple'] = 100
    print(my_dict) # {'apple': 100, 'list': [1, 2, 3], 'banana': 50}
```
- 언제 딕셔너리 사용?
  - 데이터에 순서 필요 없고, 각 데이터에 의미 있는 이름 붙여 관리하고 싶을 때 사용
  - ex. 사람의 인적 정보, 게임 캐릭터의 능력치 등
  - API할 때 서버에서 딕셔너리 형태 데이터 줌


# set

## ✏️set
- **순서와 중복이 없는** **변경 가능한** 자료형
- 세트 표현
  - 중괄호 { }안에 값들을 쉼표(,)로 구분하여 만듦
  - 수학에서의 집합과 동일한 연산 처리 가능
- 세트의 두 가지 핵심 특징
  1. 중복 허용 X : 똑같은 값은 단 하나만 존재
  2. 순서 없음 : 인덱싱(set[0])이나 슬라이싱(set[0:2]) 사용 불가
- 비어있는 딕셔너리와의 혼동 피하기 위해, 비어있는 세트는 set() 함수 생성
```python
    my_set_1 = set()
    my_dict = {}
    my_set_2 = {1, 2, 3}
    my_set_3 = {1, 1, 1}

    print(my_set_1) # set()
    print(my_set_2) # {1, 2, 3}
    print(my_set_3) # {1}
```

## ✏️세트의 집합 연산
- 세트는 수학의 '집합' 개념 그대로 가져옴
- 두 데이터 그룹 간 관계 파악하는데 매우 효과적
```python
    my_set_1 = {1, 2, 3}
    my_set_2 = {3, 6, 9}
    #합집합
    print(my_set_1 | my_set_2) # {1, 2, 3, 6, 9}
    #차집합
    print(my_set_1 - my_set_2) # {1, 2}
    #교집합
    print(my_set_1 & my_set_2) # {3}
```


# Other types

## ✏️None
- 파이썬에서 '값이 없음'을 표현하는 특별한 데이터 타입
- 마치 내용물 없는 '빈 상자'와 같음
- 숫자 0이나 빈 문자열(' ')과는 다른, '값이 존재하지 않음' 또는 '아직 정해지지 않음'이라는 상태 나타내기 위해 사용

## ✏️Boolean
- '참(True)'과 '거짓(False)' 단 두 가지 값만 가지는 데이터 타입
  > 컴퓨터의 본질과 유사 (0과 1)
- 마치 on/off 스위치처럼, 조건문에서 "맞다" 또는 "틀리다" 판단하는 역할
- 비교/논리 연산의 평가 결과로 사용
- 주로 조건/반복문과 함꼐 사용 예정


# Collection

## ✏️Collection
- 여러 개의 값을 하나로 묶어 관리하는 자료형들을 통칭하는 말
- 여러 물건 담는 '보관함'과 같음, 파이썬은 목적에 따라 다양한 종류의 컬렉션 제공
- str, list, tuple, range, set, dict 데이터 타입 모두 collection에 분류

|컬렉션명|변경 가능 여부|순서 존재 여부|
|:---:|:---:|:---:|
|str|X|O|
|list|O|O|
|tuple|X|O|
|dict|O|X|
|set|O|X|


## ✏️불변과 가변
- 컬렉션 타입은 생성 후 내용 변경 가능 여부에 따라 '불변'과 '가변' 두 그룹으로 나뉨
- [pythontutor](https://pythontutor.com/python-compiler.html#mode=edit)에서 메모리 참조 비교해보기
|구분|불변(Immutable)|가변(Mutable)|
|:---:|:---:|:---:|
|특징|변경 불가, 안전성, 예측 가능|변경 가능, 유연성, 효율성|
|종류|str, tuple, range|list, dict, set|


# 형변환

## ✏️형변환
- 한 데이터 타입을 다른 데이터 타입으로 변환하는 과정
- '형태'를 필요에 따라 바꾸는 것
- 2가지 종류
  - 암시적 형변환: 파이썬이 자동으로 처리
  - 명시적 형변환: 개발자가 직접 지시

## ✏️암시적 형변환
- 파이썬이 연산 중에 자동으로 데이터 타입을 변환
- 파이썬이 데이터 손실 막기 위해 더 정밀한 타입으로 자동 변환해주는 규칙
- 개발자가 신경쓰지 않아도 **더 안전한 쪽으로** 파이썬이 처리
- 암시적 형변환 예시
  - 정수와 실수의 연산에서 정수가 실수로 변환
  - Boolean과 Numeric Type에서만 가능
    ```python
        print(3 + 5.0) # 8.0
        print(True + 3) # 4
        print(True + False) # 1
    ```

## ✏️명시적 형변환
- 개발자가 변환하고 싶은 타입을 직접 함수로 지정하여 변환
- 서로 다른 타입의 데이터를 '호환'되도록 맞추는 과정
- 파이썬은 타입에 엄격해서, 정수와 문자열을 바로 더할 수 없음
- 명시적 형변환 예시
    |함수|설명|예시|결과|
    |:---:|:---:|:---:|:---:|
    |int()|정수로 변환|int("123")|123|
    |float()|실수로 변환|float("3.14")|3.14|
    |str()|문자열로 변환|str(100)|"100"|
    |list()|리스트로 변환|list("abc")|['a', 'b', 'c']|
    |tuple()|튜플로 변환|tuple([1, 2])|(1, 2)|
    |set()|세트로 변환|set([1, 2, 2])|{1, 2}|
- str -> int : 형식에 맞는 숫자만 가능
- int -> str : 모두 가능

# 연산자

## ✏️산술 연산자
- 수학적 계산을 위해 사용되는 연산자

## ✏️복합 연산자
- 연산과 할당이 함께 이뤄짐
  |기호|예시|의미|
  |:--:|:--:|:--:|
  |+=|a += b|a = a + b|
  |-=|a -= b|a = a - b|
  |*=|a *= b|a = a * b|
  |/=|a /= b|a = a / b|
  |//=|a //= b|a = a // b|
  |%=|a %= b|a = a % b|
  |**=|a **= b|a = a ** b|

## ✏️비교 연산자
- 두 값을 비교하여 그 관계가 맞는지 틀리는지 True 또는 False로 반환
  |기호|내용|
  |:--:|:--:|
  |<|미만|
  |<=|이하|
  |>|초과|
  |>=|이상|
  |==|같음|
  |!=|같지 않음|
  |is|같음|
  |is not|같지 않음|
- == 연산자
  - 값(데이터)이 같은지 비교
  - 동등성(equality)
  - 1 == True -> True
- is 연산자
  - 객체 자체가 같은지 비교
  - 식별성(identity)
  - 두변수가 완전히 동일한 객체 가리키는지, 즉 메모리 주소가 같은지 확인할 때 사용
- is 대신 ==를 사용해야 하는 이유
  - 결론: is는 '정체성'을, ==는 '가치'를 비교하기 때문
  - 두 연산자는 "같다"를 확인하는 목적이 근본적으로 다름
    - is 는 '정체성(identity)'이 같은지 확인
    - == 는 '값(Value)'이 같은지 확인
- is를 값 비교에 사용하면 안되는 이유 - "의도와 다른 결과"
  - is는 " 두 객체가 메모리상에서 같은 존재인가?"를 묻기 때문에 False
  - "두 객체의 값이 논리적으로 같은가?"가 궁금하므로 ==를 사용해야 의도에 맞는 True 출력
- is 연산자는 싱글턴 객체 비교할 때 사용
  > #### 싱글턴(Singleton) 객체
  > - 특정 값에 대해 파이썬 전체에서 단 하나의 객체만 생성되어 재사용되는 특별한 객체
  > - 여러 변수가 이 값을 가지더라도, 모두 미리 만들어진 하나의 객체를 함께 가리키므로 항상 같은 메모리 주소
  > - 파이썬 대표 싱글턴 객체 : None, True, False
- 리스트나 객체 비교 시 주의사항
```python
    a = [1, 2, 3]
    b = [1, 2, 3]

    print(a == b) #True (두 리스트의 값은 동일)
    print(a is b) #False (서로 다른 리스트 객체)

    b = a
    print(a is b) #True (같은 객체 가리킴)
```
> ### ==와 is 정리
> - 값 비교에는 == 사용, 객체(레퍼런스) 비교에는 is 사용 원칙
> - 숫자나 문자열, 불리언 값 등 동등성(값) 판단해야 할 때 is 쓰면 False 나올 수 있음
> - is는 주로 싱글턴 객체에 대한 비교 시 사용


## ✏️논리 연산자
- 여러 개의 조건 조합하거나, True/False 값 반대로 뒤집을 때 사용
  |기호|연산자|내용|
  |:--:|:--:|:--|
  |and|논리곱|두 피연산자 모두 True일 때 전체 표현식 True|
  |or|논리합|두 피연산자 하나라도 True일 때 전체 표현식 True|
  |not|논리부정|단일 피연산자 부정|

## ✏️단축 평가
- 논리 연산에서 두 번째 피연산자를 평가하지 않고 결과 결정하는 동작
- 컴퓨터는 꼭 필요한 계산만 하고, 결과가 이미 정해지면 뒤에 있는 코드까지 확인 X
- 파이썬의 '참(True)'과 '거짓(False)'에 대한 새로운 시각
  - 거짓으로 취급되는 값들 : False, 숫자 0, 빈 문자열 "", 빈 리스트 [ ], None 등
  - 참으로 취급되는 값들 : True 그리고 '거짓'이 아닌 모든 값, 내용이 있는 값
- 단축 평가 동작 정리
  - and 연산자
    - 하나라도 '거짓'이면 바로 '거짓'
    - and는 연산을 -> 으로 진행, **처음 만나는 '거짓' 값 바로 반환**
    - 끝까지 갔는데 모든 값이 '참'이면, **맨 마지막 '참' 값을 반환**
  - or 연산자
    - 하나라도 '참'이면 바로 '참'
    - or는 연산을 -> 으로 진행, **처음 만나는 '참' 값 바로 반환**
    - 끝까지 갔는데 모든 값이 '거짓'이면, **맨 마지막 '거짓' 값을 반환**
  - 단축 평가 하는 이유
    - 코드 실행 최적화, 불필요한연산 피할 수 있도록 함
    - 단순히 True/False 논리 연산 넘어, 코드의 흐름 제어, 오류 방지, 간결한 코드 작성 시 매우 유용하게 사용되는 파이썬의 중요한 기능

## ✏️멤버십 연산자
- 특정 값이 시퀀스나 다른 컬렉션 안에 포함되어 있는지 확인하는 연산자
  |기호|내용|
  |:--:|:--|
  |in|왼쪽 피연산자가 오른쪽 피연산자의 시퀀스에 속하는지 확인|
  |not in|왼쪽 피연산자가 오른쪽 피연산자의 시퀀스에 속하지 않는지 확인|

## ✏️시퀀스형 연산자
- 시퀀스 자료형(문자열, 리스트, 튜플)에 특별한 의미로 사용되는 연산자
- '+'는 시퀀스 연결하는 기능, '*'는 시컨스 반복하는 기능
  |연산자|내용|
  |:--:|:--:|
  |+|결합 연산자|
  |*|반복 연산자|

## ✏️연산자 우선순위
`( )`(grouping) > `[ ]`(인덱싱, 슬라이싱) > `**` > `+, -`(양,음수) > `*, /, //, %` > `+, -` > `<, <=, >, >=, ==, !=` > `is, is not` > `in, not in` > `not` > `and` > `or`


# 참고

## ✏️Trailing Comma (후행 쉼표)
- 컬렉션의 마지막 요소 뒤에 붙는 쉼표
- 일반적으로 Trailing Comma 작성은 선택사항
- 단, 하나의 요소로 구성된 튜플은 필수
- 기본 규칙
  - 각 요소를 별도의 줄에 작성
  - 마지막 요소 뒤에 Trailing comma 추가
  - 닫는 괄호는 새로운 줄에 배치
- 장점
  - 가독성 향상 (dict에서 많이 사용)
    - 각 줄이 동일한 패턴 가짐
    - 코드 리뷰 용이
  - 유지보수 용이성
    - 항목 추가/제거가 간단
    - 실수로 인한 구문 오류 방지