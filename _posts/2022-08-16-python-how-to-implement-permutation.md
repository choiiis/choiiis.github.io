---
title: "Python 재귀함수로 순열 구현하기"
excerpt: "itertools 없이 순열을 구현해보자"

categories:
  - Python
tags:
  - [Python]

permalink: /python/how-to-implement-permutation/

toc: true
toc_sticky: true

date: 2022-08-16
last_modified_at: 2022-08-16
---

Python으로 재귀함수를 이용해서 n개 원소의 순열을 구해보자.  
itertools 라이브러리의 permutations 함수를 쓸 수도 있지만,  
재귀함수만으로도 구현할 수 있다.

## 소스코드

```python
def recur(lst):
  if len(lst) == n:
    print(lst)
  else:
    for i in range(1, n+1):
      if visit[i-1] == 0:
        visit[i-1] = 1
        lst.append(i)
        recur(lst)
        lst.pop()
        visit[i-1] = 0
  return

n = int(input())
ans = []
visit = [0, 0, 0, 0] # 원소 중복 방지
recur(ans)
```

## 실행결과

![output](/assets/images/posts_img/python-how-to-implement-permutation/output.png)
