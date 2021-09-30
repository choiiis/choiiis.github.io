---
title: "BOJ 백준 5585 거스름돈 (C++)"
excerpt: "BOJ 백준 5585 거스름돈 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-5585/

toc: false
 
date: 2020-05-27
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 5585 C++ 풀이 코드 : Greedy

```cpp
#include <iostream>

using namespace std;
int main(void) {
    int cost;
    int coin_num = 0; // the total number of coin
    cin >> cost;

    int change = 1000 - cost;
    int coin[6] = { 500, 100, 50, 10, 5, 1 };
    
    for(int i = 0; i < 6; i++){
        int tmp = 0;
        
        // no more change. finish
        if (change == 0) {
            break;
        }

        if (change >= coin[i]) {
            // tmp : the number of coin[i]
            tmp = change / coin[i];
            coin_num += tmp;
            change -= tmp * coin[i];

        }
    }

    cout << coin_num << endl;

    return 0;
}
```

---

## 회고

금방 풀었지만 change >= coin[i] 에서 = 을 빼서 처음에 제출 실패가 떴다.