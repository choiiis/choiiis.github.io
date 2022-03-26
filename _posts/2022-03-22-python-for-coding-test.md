---
title:  "코딩테스트를 위한 Python 정리"
excerpt: "코딩테스트 문제를 해결하면서 정리한 Cheat Sheet"

categories:
  - Python
tags:
  - [Python]

permalink: /python/for-coding-test/

toc: true
# toc_sticky: true

date: 2022-03-22
last_modified_at: 2022-03-22
---

문제를 풀면서 자주 찾아보거나 기억할 만한 내용 정리하기
2022.03.07 ~ 추가중

## 자료형과 내장 함수

### 정수형, 실수형, 복소수형

python에서는 소수점 붙인 수를 대입하면 실수형으로 처리

```python
a = 5.
b = .7
print(a) # 5.0
print(b) # 0.7
print(type(a)) # <class 'float'>
print(type(b)) # <class 'float'>
```

#### 실수 표현 정확도 한계
```python
a = 0.3 + 0.6
if a == 0.9:
  print(True)
else:
  print(False)
 # 결과 : False
```

해결 방법 : round 함수 권장

```python
# round(수, 자리 수) 반올림
a = round(0.3 + 0.6, 1)  # 0.9
```

첫 줄을 이렇게 바꾸면 정상 동작한다.

---

## str, list, tuple, dict, set

### 클래스  요약

#### str

생성 : "" or ''
ex. "Hello" or 'world'
- 인덱싱, 슬라이싱 가능
- 특정 인덱스 값 변경 불가 (immutable)
  
#### list

생성 : \[\] or list() 
ex. \[1, 2, 3\] or list(\[1, 2, 3\])
- 인덱싱, 슬라이싱 가능 (순서가 있음)
- 원소 중복 가능
- 특정 인덱스 값 변경 가능 (mutable)
- 원소 추가(append, insert) 제거(remove) 가능

#### tuple

생성 : () or tuple()
ex. (1, 2, 3) or tuple((1, 2, 3))
- 인덱싱, 슬라이싱 가능 (순서가 있음)
- 원소 중복 가능
- 특정 인덱스 값(=한번 선언된 값) 변경 불가 (immutable)
- 원소 추가(append, insert) 제거(remove) 불가

#### dict

생성 : {} or dict() 
ex. {'name': 'Min', 'age': 12} / dict({'name': 'Min', 'age': 12})
- 'key' : 'value'의 쌍을 데이터로 갖는 자료형
- 인덱싱 불가 (순서가 없음)
- 'key'는 중복 불가. 중복 시 뒤에 선언된 값 사용
- dict 원소 추가, 삭제 가능
- 'key'값으로 'value'값 조회, 수정 O(1) → 리스트보다 성능이 좋음
- 키와 값의 자료형 모두 통일하지 않아도 되고 섞어서 사용 가능


#### set

생성 : list, 문자열 이용하여 초기화 or {1, 2, 3} or s = set() 
→ 빈 중괄호 {}는 dict 클래스가 생성되므로 주의
- 인덱싱 불가 (순서가 없음) → for i in s 로 출력해보면 어떤 값이 먼저 나올지 모름
- 원소 중복 불가 (key 값)
- 원소 추가, 제거, 조회 가능
- 원소로 조회 O(1)
- default가 오름차순 정렬

---

### 문자열 (str)

#### 문자열 내장함수

▶ lower

```python
s = "HapPineSS"
# 소문자 casting된 문자열 반환
print(s.lower()) # happiness
print(s) # HapPineSS (원본 문자열 변경 X)
```

▶ upper

```python
# 대문자 casting된 문자열 반환
print(s.upper()) # HAPPINESS
```

▶ find

```python
# "s"가 위치한 index 찾기
# 여러 개일 경우 가장 앞쪽 index
print(s.find("s")) # 7
```

▶ count

```python
# 문자열 내의 "s"의 개수
print(s.count("s")) # 2
```

#### 문자열 활용하기

문자열 2개 연결하기

```python
a = "ABC" + "DEF"
b = "Hello"
c = "World"
print(a) # ABCDEF
print(b + " " + c) # Hello World
```

---

### 리스트 (list)

#### 빈 리스트 생성 방법

```python
a = []
b = list()
```

2가지 모두 빈 리스트가 생성된다.

#### 리스트 생성과 동시에 초기화
```python
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 생성
arr = list(range(1, 11))
```

#### 리스트 2개 연결
```python
arr1 = [1, 2]
arr2 = [3, 4, 5]
arr = arr1 + arr2 # [1, 2, 3, 4, 5]
```

#### 빈 리스트 대입 주의
```python
arr = []
for i in range(5):
  arr[i] = i
```

빈 리스트에 대입은 불가능하다. 리스트를 적당한 크기로 초기화하거나 append로 추가해야 한다.

#### 리스트 내장함수

▶ append

```python
# init
a = [1, 2, 3, 4, 5]
# a.append(v) : 맨 뒤에 v 추가
a.append(6) # [1, 2, 3, 4, 5, 6]
```

▶ insert

```python
# a.insert(i, v) : i번 인덱스에 v 추가
a.insert(3, 7) # [1, 2, 3, 7, 4, 5, 6]
```

▶ pop

```python
# a.pop() : 마지막 원소 꺼내기 (꺼낸 값 반환)
# a.pop(i) : i번 인덱스 값 꺼내기 (꺼낸 값 반환)
print(a.pop()) # 6
print(a) # [1, 2, 3, 7, 4, 5]
print(a.pop(3)) # 7
print(a) # [1, 2, 3, 4, 5]
```

▶ remove

```python
# a.remove(v) : v 값을 찾아서 제거
# 없는 값을 제거할 경우 ValueError: list.remove(x): x not in list 에러 발생
a.remove(4) # [1, 2, 3, 5]

# 참고) 특정 index의 값을 제거하려면 del 키워드 사용
del a[2] # 2번 index 원소 삭제
```

▶ index

```python
# a.index(v) : v가 리스트의 몇 번째 index에 있는지 반환
print(a.index(5)) # 3
```

▶ min, max, sum

```python
sum(a) # a의 모든 원소의 합
max(a) # a의 원소 중 최대 값
min(a) # a의 원소 중 최소 값
```

▶ sort

```python
a = [1, 3, 2, 7, 5]
# 원본 리스트 정렬 (리스트 a 자체 정렬)
a.sort() # 오름차순 [1, 2, 3, 5, 7]
a.sort(reverse=True) # 내림차순 [7, 5, 3, 2, 1]

# 정렬된 새로운 리스트 반환 (리스트 a는 원본 유지, 정렬된 리스트 b로 반환)
a = [1, 3, 2, 7, 5]
b = sorted(a)
c = sorted(a, reverse=True) # 내림차순
print(a) # [1, 3, 2, 7, 5]
print(b) # [1, 2, 3, 5, 7]
print(c) # [7, 5, 3, 2, 1]

```

▶ reverse

```python
a = [1, 3, 2, 7, 5]
# 리스트 원소 순서 뒤집기
a.reverse() # [5, 7, 2, 3, 1]
```

▶ clear

```python
a.clear() # 빈 리스트로 만들기
```

#### 리스트 활용하기

▶ len

```python
a = [1, 2, 3, 4]
len(a) # 리스트 원소의 개수 출력. 4

for i in range(len(a)):
  print(a[i])
  
for x in a:
  print(x)
```

▶ enumerate

```python
a = [12, 19, 34, 21, 50]
for x in enumerate(a):
  print(x) # (0, 12)\n (1, 19)\n ... (4, 50)\n 튜플로 출력

for x in enumerate(a):
  print(x[0], x[1]) # 0 12\n 1 19\n ... 4 50\n 
  
for i, val in enumerate(a):
  print(i, val) # 0 12\n 1 19\n ... 4 50\n
```

▶ all, any

```python
a = [11, 12, 42, 38, 7]
# all(iterable 리스트, 튜플, 딕셔너리 등)
# 모든 요소가 참이면 True, 하나라도 거짓이면 False
a = [11, 12, 42, 38, 7]
if all(60 > x for x in a):
  print("모든 원소가 60 미만입니다.")

# all(iterable 리스트, 튜플, 딕셔너리 등)
# 요소가 하나라도 참이면 True, 전부 거짓이면 False
if any(10 > x for x in a):
  print("20미만인 원소가 존재합니다.")
```

---

### 2차원 리스트

#### 2차원 리스트 초기화

```python
# N*M 2차원 리스트 초기화 할 때 (세로 N & 가로 M)
array = [[0]*m for _in range(n)]
```

---

### 튜플 (tuple)

#### 튜플 생성 및 초기화

```python
t = (1, 2, 3, 4, 5)
```

#### 튜플에 원소 추가

튜플은 원칙적으로 선언된 값 수정 불가. 따라서 append, insert 함수 없음.
따라서 아래와 같이 튜플 여러 개를 연결하여 새로운 튜플을 생성하는 방식을 활용

```python
t1 = (1, 2, 3)
t2 = (4, 5)
t3 = t1 + t2
```

#### 튜플 인덱스로 값 조회

```python
print(t[3]) # 4
print(t[1:4]) # (2, 3, 4)
t[3] = 2 # Error. 변경 불가
```

#### 튜플 값 존재 여부 확인

```python
print(1 in t) # True
print(9 in t) # False
```

#### 튜플 내장함수

▶ count

```python
t = (1, 2, 2, 3, 3, 4)
# tuple.count(v) v 값의 개수 반환
t.count(2) # 2
```

▶ index

```python
# tuple.index(v) 특정 값의 인덱스 반환. 
# 여러 개면 가장 앞쪽 인덱스, 없으면 에러
s.index(2) # 1
```

---

### 딕셔너리 (dict)

- 'key'로 문자열, 정수형, 실수형, 불린형 모두 사용 가능
- 'value'로는 추가로 리스트, 딕셔너리까지도 사용 가능

#### 딕셔너리 초기화

```python
data = dict()
data['사과'] = 'Apple'
data['바나나'] = 'Banana'
data['코코넛'] = 'Coconut'
```

#### 딕셔너리 key만, value만 리스트로

```python
data.keys() # key만
data.values() # value만
```

---

### 집합 (set)

#### set 내장함수

▶ add

```python
s = {1, 2, 3}
# set.add(v) 새로운 원소 추가
s.add(4) # {1, 2, 3, 4}
```

▶ update

```python
# set.update(v) 새로운 원소 여러 개 추가 (수정 보다는 여러 개 추가 개념)
s.update([5,7]) # {1, 2, 3, 4, 5, 7}
```

▶ remove

```python
a = {1, 2, 3}
# set.remove(v) 원소 삭제
s.remove(4) # {1, 2, 3, 5, 7}
```

---

## Python 코테 cheat sheet

### 한 줄에 여러 개의 숫자 입력 받기

```python
'''
[입력 예시]
1 2 3 4
'''
a, b, c, d = map(int, input().split())
print(a, b, c, d) # 1, 2, 3, 4
```

---

### 리스트 원소 한 줄로 입력 받기

```python
'''
[입력 예시]
1 3 5 7 9 10
'''
a = list(map(int, input().split()))
print(a) # [1, 3, 5, 7, 9, 10]

'''
[입력 예시]
A B C D E
'''
a = list(input().split())
print(a) # ['A', 'B', 'C', 'D', 'E']
```

---

### 리스트 중복 제거 & 정렬

```python
a = [3, 1, 5, 8, 5, 10, 7, 1]
print(a)
b = list(set(a)) # [1, 3, 5, 7, 8, 10]
c = sorted(list(set(a))) # [1, 3, 5, 7, 8, 10]
d = sorted(list(set(a)), reverse=True) # [10, 8, 7, 5, 3, 1]
```

set으로 변경하여 다시 list로 변경하면 중복이 제거된다. 인덱스로 값을 찾아야 하는 경우가 아니라면 list로 다시 변경하는 부분은 없어도 된다.

set으로 변경하기만 해도 오름차순 정렬이 되기도 하는데 원소가 많은 경우 제대로 정렬이 안되는 케이스가 발생했었다. 그래서 확실하게 sorted 처리를 해주면 좋다.

---

### 리스트 전체 합과 평균 구하기

```python
N = int(input()) # 개수
a = list(map(int, input().split())) # 점수 리스트 입력
total = sum(a)
avg = int(round(total/N, 0)) # 평균을 첫째 자리에서 반올림
```

c언어 습관 때문에 리스트 합 구할 때 for문 쓰게 됨. Python에서는 sum이라는 아주아주 편한 내장 함수가 있다.

---

### 리스트 반복문에서 리스트의 원소 여러 번 사용할 때

```python
score = [80, 83, 95, 87, 93, 71]
for i, val in range(N):
  if val < 90: # "score[i] < 90" 대신 짧고 편하게 사용 가능
    print("B")
  elif val < 80:
    print("C")
  elif val < 70:
    print("D")
```

---

### 리스트 원소 개수 세기 (딕셔너리 활용)

```python
s = [1, 3, 4, 2, 3, 4, 1, 3]
cnt = {} # dictionary 생성
for x in s:
  if x in cnt:
    cnt[x] += 1
  else:
    cnt[x] = 1
```

---

### 딕셔너리 value로 key값 찾기

```python
for key, value in cnt.items():
  if value == "찾을 value 값":
    print(key, end=' ') # value에 해당하는 key 값 출력
```

---

### 리스트를 문자열로 변환하기

```python
arr = ['H', 'a', 'P', 'p', 'Y']
print(type(''.join(arr))) # <class 'str'>
a = ['0', '1', '3', '6']
print(int(''.join(a))) # 136
```

---

### 두 변수 값 바꾸기 (swap)

```python
a, b = b, a # 한 줄로 가능!
```

---

### 연속하는 값들을 합하여 M이 되는 경우의 수

lt_idx와 rt_idx를 (왼쪽 끝 idx, 오른쪽 끝 idx) 지정하고,
합이 M보다 크면 lt에 1을 더하고 작으면 rt에 1을 더하면서 한 칸씩 이동

---

### 딕셔너리 'key'로 존재 여부 확인

```python
if '사과' in data:
  print("yes")
```

---

### 딕셔너리를 key 또는 value 기준으로 정렬

```python
a = {'Tom': 90, 'Liz': 75, 'John': 67, 'Mia': 92}

print(a.keys()) # dict_keys(['Tom', 'Liz', 'John', 'Mia'])
print(list(a.keys())) # ['Tom', 'Liz', 'John', 'Mia']
print(sorted(a.keys())) # ['John', 'Liz', 'Mia', 'Tom']
print(sorted(a.keys(), reverse=True)) # ['Tom', 'Mia', 'Liz', 'John']

# 튜플 자료형으로 리턴
print(sorted(a.items())) 
# 결과 : [('John', 67), ('Liz', 75), ('Mia', 92), ('Tom', 90)]
print(sorted(a.items(), reverse=True)) 
# 결과 : [('Tom', 90), ('Mia', 92), ('Liz', 75), ('John', 67)]

# 람다식 key값 기준 정렬
print(sorted(a.items(), key=lambda x: x[0])) 
# 결과 : [('John', 67), ('Liz', 75), ('Mia', 92), ('Tom', 90)]
print(sorted(a.items(), key=lambda x: x[0], reverse=True)) 
# 결과 : [('Tom', 90), ('Mia', 92), ('Liz', 75), ('John', 67)]

# 람다식 value값 기준 정렬
print(sorted(a.items(), key=lambda x: x[1]))
# 결과 : [('John', 67), ('Liz', 75), ('Tom', 90), ('Mia', 92)]
print(sorted(a.items(), key=lambda x: x[1], reverse=True))
# 결과 : [('Mia', 92), ('Tom', 90), ('Liz', 75), ('John', 67)]
```

참고 : [https://codingpractices.tistory.com/36](https://codingpractices.tistory.com/36)

---

### 2차원 리스트 입력 받기

```python
'''
[입력 예시]
5
0 2 1 1 0
1 1 1 1 2
0 2 1 2 1
0 2 1 1 0
0 1 1 1 2
'''
n = int(input())
arr = list(list(map(int, input().split())) for _ in range(n))
```

---

### 이분 탐색

중앙값을 찾아서 비교해서 중앙값 전/후로 나누어서 다시 탐색을 반복

```python
a.sort() # 먼저 정렬
lt = 0 # 시작 값
rt = n-1 # 끝 값

while lt <= rt:
  mid = (lt + rt) // 2
  if a[mid] < m:
    lt = mid + 1
  elif m < a[mid]:
    rt = mid - 1
  elif m == a[mid]:
    print(mid+1)
    break
```

---

### max, min python스럽게 구하기

```python
max_val = max(max_val, tmp)
min_val = min(min_val, tmp)
```

---

### python list 2개로 dictionary를 생성하기

```python
key = ['Alex', 'Jess', 'Dilan', 'Mei', 'Teddy']
value = [80, 90, 95, 67, 88]
key_val = [key, value]
landmark_dict = dict(zip(*key_val))

# 결과 : {'Alex': 80, 'Jess': 90, 'Dilan': 95, 'Mei': 67, 'Teddy': 88}
```
---

### python list가 비어있는지 확인

```python
arr = []

if not arr:
  print("empty")

if arr:
  print("not empty")
```

---

### python list의 마지막 요소 가져오기/제거하기

```python
arr = [1, 3, 5, 2, 4]
print(arr[-1]) # 4
arr.pop()
```

c언어 stack 클래스의 함수 stack.top() 대신 [-1]로 마지막 원소 접근한다. pop() 함수는 python도 동일하게 사용


