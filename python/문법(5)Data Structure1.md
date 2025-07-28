# Data Structure

## 개요
- 여러 데이터를 효과적으로 사용 관리하기 위한 구조
- str, list, dict 등
- 자료구조
    - 컴퓨터 공학에서는 '자료구조'라고 함
    - 각 데이터의 효율적인 저장, 관리를 위한 구조를 나눠 놓은 것
    - 단순히 데이터 묶는 것을 넘어, 프로그램의 성능과 효율성, 유지보수성에 큰 영향 미치는 핵심적인 개념
- 데이터 구조의 활용
    - 메서드 : 각 데이터 구조의 메서드를 호출하여 다양한 기능 활용
    - 문자열, 리스트, 딕셔너리 등 파이썬의 다양한 데이터 구조는 저마다의 고유 메서드 가짐
    - 이 메서드들은 해당 데이터 구조의 데이터 효율적으로 조작, 특정 기능 수행하기 위해 제공

## 메서드
- 객체에 속한 함수, 객체가 특정 작업을 수행하도록 정의된 함수
- 메서드는 클래스(class) 내부에 정의되는 함수
- 클래스는 파이썬에서 '타입 표현하는 방법'이며 이미 은연중에 사용중
- help 함수 통해 str 호출하면class 였다는 것을 확인
-> **메서드는 어딘가(클래스)에 속해 있는 함수, 각 데이터 타입별로 다양한 기능을 가진 메서드 존재**
- 메서드 호출 방법
    - `데이터타입 객체.메서드()` : 우리가 만든 객체(데이터)에게 원하는 명령(메서드) 내리는 방법
    - ex. `a_list.append(2)`

<br>

# 시퀀스 데이터 구조

## 문자열
- 문자열 조회/탐색 및 검증 메서드
    - `.find(x)` : x의 첫 번째 위치 반환. 없으면 -1 반환.
    ```python
        print('banana'.find('a')) # 1
        print('banana'.find('z')) # -1
    ```
    - `.index(x)` : x의 첫 번째 위치를 반환. 없으면 오류 발생.
    ```python
        print('banana'.find('a')) # 1
        print('banana'.find('z')) # VlueError: substring not found
    ```
    - `.isupper(), .islower()` : 문자열이 모두 대문자/소문자로 이루어져 있는지 확인
    ```python
        string1 = 'HELLO'
        string2 = 'Hello'
        print(string1.isupper()) # True
        print(string2.isupper()) # False
        print(string1.islower()) # False
        print(string2.islower()) # False
    ```
    - `.isalpha()` : 문자열이 알파벳으로만 이루어져 있는지 확인
    ```python
        string1 = 'Hello'
        string2 = '123heis98576ssh'
        print(string1.isalpha()) # True
        print(string2.isalpha()) # False
    ```
- 문자열 조작 메서드(**새로운 문자열 반환**) -> 불변객체라 원본 못바꿈
    - `.replace(old, new[, count])` : 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
    - `count` 는 바꿀 개수
    > ### 📌문법에서 
    > `< >`는 필수 입력
    > 
    > `[ ]`는 선택 사항
        ```python
        text = 'Hello, world! world world'
        new_text1 = text.replace('world', 'Python')
        new_text2 = text.replace('world', 'Python', 1)
        print(new_text1) # Hello, Python! Python Python
        print(new_text2) # Hello, Python! world world
    ```
    - `.strip([chars])` : 문자열의 시작과 끝에 있는 공백 혹은 지정한 문자 제거
    ```python
         text = '   Hello, world!   '
         new_text = text.strip()
         print(new_text) # 'Hello, world!'
    ```
    - `.split(sep=None, maxsplit=-1)` : sep(separator)를 구분자 문자열로 사용하여 문자열에 있는 단어들의 리스트 반환
    ```python
        text = 'Hello, world!'
        words1 = text.split(',')
        words2 = text.split()
        print(words1) # ['Hello', ' world!'] -> sep을 ,으로 설정하여 world! 앞에 공백 포함되어 있음
        print(words2) # ['Hello,', 'world!'] -> sep을 아무것도 안넣으면 공백으로 구분
    ```
    - **`'separator'.join(iterable)`** : iterable(반복 가능)의 문자열을 연결한 문자열 반환
    ```python
        words = ['Hello', 'world!']
        text = '-'.join(words)
        print(text) # 'Hello-world!'
    ```
    - 문자열 조작 메서드
    ```python
        text = 'heLLo, woRLd!'
        new_text1 = text.capitalize()
        new_text2 = text.title()
        new_text3 = text.upper()
        new_text4 = text.lower()
        new_text5 = text.swapcase()

        print(new_text1) # Hello, world!
        print(new_text2) # Hello, World!
        print(new_text3) # HELLO, WORLD!
        print(new_text4) # hello, world!
        print(new_text5) # HEllO, WOrLD!
    ```

## 리스트
- 리스트 값 추가 및 삭제 메서드 **-> 원본을 조작 -> 반환값 없음**
    - **`.append(x)`** : 리스트 **마지막**(우측 끝)에 항목 x를 추가
    ```python
        my_list = [1, 2, 3]
        my_list.append(4)
        print(my_lsit) # [1, 2, 3, 4]
    ```
    - `.extend(iterable)` : 리스트에 다른 반복 가능한 객체의 모든 항목 추가
    ```python
        my_list = [1, 2, 3]
        my_list.extend([4, 5, 6])
        print(my_lsit) # [1, 2, 3, 4, 5, 6]
    ```
    - extend 주의사항 : 
        1. append는 리스트이던 정수이던 그냥 하나를 넣음
        2. 반복 가능한 객체 아니면 추가 불가
    - `.insert(i, x)` : 리스트의 지정한 인덱스 i 위치에 항목 x를 삽입
    ```python
        my_list = [1, 2, 3]
        my_list.insert(1, 5)
        print(my_list) # [1, 5, 2, 3]
    ```
    - `.remove(x)` : 리스트에서 첫 번째로 일치하는 항목 삭제
    ```python
        my_list = [1, 2, 3, 2, 2, 2]
        my_list.remove(2)
        print(my_list) # [1, 3, 2, 2, 2]
    ```
    - **`.pop(i)`** : 리스트에서 지정한 인덱스의 항목 제거하고 **반환**. 작성하지 않을 경우 마지막 항목 제거
    ```python
        my_list = [1, 2, 3, 4, 5]
        item1 = my_list.pop()
        item2 = my_list.pop(0)
        print(item1) # 5
        print(item2) # 1
        print(my_list) # [2, 3, 4]
    ```
    - `.clear()` : 리스트의 모든 항목(요소) 삭제
    ```python
        my_list = [1, 2, 3]
        my_list.clear()
        print(my_list) # []
    ```
- 리스트 탐색 및 정렬 메서드
    - `.index(x)` : 리스트에서 첫 번째로 일치하는 항목 x의 **인덱스 반환**
    ```python
        my_list = [1, 2, 3]
        index = my_list.index(2)
        print(index) # 1
    ```
    - `.count(x)` : 리스트에서 항목 x의 개수 반환
    ```python
        my_list = [1, 2, 2, 3, 3, 3]
        count = my_list.count(3)
        print(count) # 3
    ```
    - **`.revers()`** : 리스트의 순서를 역순으로 변경(**정렬X**)
    ```python
        my_list = [1, 3, 2, 8, 1, 9]
        my_list.reverse()
        print(my_list) # [9, 1, 8, 2, 3, 1]
        print(my_list.reverse()) # None
    ```
    - `.sort()` : 원본 리스트를 오름차순으로 정렬
    ```python
        my_list = [3, 2, 100, 1]
        my_list.sort()
        print(my_list) # [1, 2, 3, 100]

        # 내림차순 정렬
        my_list.sort(reverse=True)
        print(my_list) # [100, 3, 2, 1]
    ```
- 다양한 리스트 메서드 : http://docs.python.org/3.11/tutorial/datastructures.html#data-structures

<br>

# 복사

## 객체와 참조
- 가변/불변 객체 개념
    - Mutable(가변) 객체 : 생성 후 내용 변경할 수 있는 객체 ex. list, dict, set
    - Immutable(불변) 객체 : 생성 후 내용 변경할 수 없는 객체 ex. int, float, str, tuple
- 변수 할당의 의미
    - 객체에 대한 참조를 생성하는 과정
        - 변수는 객체의 메모리 주소 가리키는 Lable 역할 함
        - 할당 시 새로운 객체 생성되거나 기존 객체에 대한 참조 생성됨
    - 새로운 객체 생성 후 참조 : 해당 객체를 메모리에 만들고, 변수가 그 객체 가리키도록 함
    - 기존 객체에 대한 참조 : 새로운 객체 만들지 않고 해당 객체에 대한 참조만 생성
- id() 함수 사용한 메모리 주소 확인
    - id() 함수 사용하여 객체의 메모리 주소 확인 가능
    - is 연산자 통해 두 변수가 같은 객체를 참조하는지 확인 가능
- 가변/불변 메모리 관리 방식
    - 가변 객체
        - 생성 후에도 그 내용 수정 가능
        - 객체의 내용이 변경되어도 같은 메모리 주소 유지
    - 불변 객체
        - 생성 후 그 값 변경 불가능
        - 새로운 값 할당하면 새 객체 생성, 변순ㄴ 새 객체 참조
- 가변/불변 메모리 관리 방식의 이유
    - 성능 최적화
        - 불변 객체: 변경 불가능하므로, 여러 변수가 동일한 객체 안전하게 공유 가능
        - 가변 객체 : 내용 수정 빈번할 때, 기존 객체 직접 수정 가능. 이로 인해 객체 생성, 삭제 비용 절감하여 성능 향상
    - 메모리 효율성
        - 불변 객체 : 동일 값 가진 여러 변수가 같은 객체 참조할 수 있어 메모리 사용 최소화 가능
        - 가변 객체 : 크기가 큰 데이터 효율적으로 수정 가능

## 얕은 복사
- 객체의 **최상위 요소**만 새로운 메모리에 복사하는 방법
- 내부에 중첩된 객체 있다면 그 객체의 참조만 복사
> ### 가변 객체
>
>
- 얕은 복사 구현 방법
    - 리스트 슬라이싱 : [:] 사용하면 원본 리스트와 동일 내용의 새 리스트 생성. 새 리스트에 복사되는 것은 해당 요소들이 참조하는 주소
    - copy() 메서드
    - list() 함수
- 얕은 복사의 한계
    - 2차원 리스트와 같이 변경 가능한 객체 안에 변경 가능한 객체 있는 경우
    - 겉의 리스트는 다른 객체이지만 안의 리스트는 주소가 같은 객체
- 1차원 리스트와 다차원 리스트에서의 차이점
    - 1차원 리스트 : 얕은 복사ㅗ 충분히 독립적인 복사본 만들 수 있음
    - 다차원 리스트 : 최상위 리스트만 복사되고, 내부 리스트는 여전히 원본과 같은 객체를 참조

## 깊은 복사
- 객체의 모든 수준의 요소를 새로운 메모리에 복사하는 방법
- 중첩된 객체까지 모두 새로운 객체로 생성됨
> ### 완전한 독립성 보장
>
>
- 깊은 복사 구현 방법 : copy 모듈에서 제공하는 deepcopy() 함수 사용
```python
    import copy
    new_object = copy.deepcopy(original_object)
```

<br>

# 참고

## List Comprehension
- 간결하고 효율적인 리스트 생성 방법
- "Pythonic"한 코드 : 파이썬 개발자들이 선호하는 스타일, 코드를 더 파이썬답게 작성하는 방법 중 하나
- List Comprehension 구조 : [표현식 for 변수 in 순회 가능한 객체 [if 조건]] or list(표현식 for 변수 in 순회 가능한 객체)
- 활용 예시
    - 2차원 배열 생성 시 (인접행렬 생성)
    ```python
        data1 = [[0]*(5) for _ in range(5)]
        # or
        data2 =[[0 for _ in range(5)] for _ in rnge(5)]
        #결과
        [[0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0]]
    ```
- comprehension을 남용하지 말자. "Simple is better than complex" "Keep it simple, stupid"

## 메서드 체이닝(Method Chaining)
- 여러 메서드를 연속해서 호출하는 방식
- 앞 메서드에 반환값이 없다면 None.메서드() 가 되어버림
- 문자열에서의 메서드 체이닝 예시
    ```python
        text = 'heLLo, woRld!'
        new_text = text.swapcase().replace('l', 'z') # 소문자 l을 소문자 z로 변경
        print(new_text) # HEzzO, WOrLD!
    ```
- 리스트에서의 메서드 체이닝 예시
    ```python
        # 잘못된 체이닝 예시 1
        numbers = [3, 1, 4, 1, 5, 9, 2]
        result = numbers.copy().sort()
        print(numbers) # [3, 1, 4, 1, 5, 9, 2] (원본 변경X)
        print(result) # None (sort() 메서드는 None 반환)
        # 잘못된 체이닝 예시 2

        # 올바른 체이닝 예시
        sorted_numbers = sorted(numbers.copy()) # sorted 함수는 반환값 존재
        print(sorted_numebrs) # [1, 1, 2, 3, 4, 5, 9]
    ```
- 메서드 체이닝 주의사항
    - 모든 메서드가 체이닝 지원 X : 메서드가 객체 반환할 때만 체이닝 가능
    - None을 반환하는 메서드는 메서드 체이닝 불가능
    - 메서드 체이닝 사용할 때는 각 메서드의 반환 값을 잘 이해하고 있어야 함.

## 문자 유형 판별 메서드
- 문자 유형 판별 메서드
    - 문자열에 포함된 문자들의 유형 판별하는 메서드
        - `isdecimal()` : 문자열 모두 숫자 문자(0~9)로만 이루어져 있어야 True
        - `isdigit()` : isdecimal()과 비슷, + 유니코드 숫자도 인식
        - `isnumeric()` : isdigit()과 유사, 몇 가지 추가적인 유니코드 문자 인식(분수, 지수, 루트 기호도 숫자로 인식)