---
title: "BOJ 백준 2468 안전 영역 (C++)"
excerpt: "BOJ 백준 2468 안전 영역 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-2468/

toc: false
 
date: 2020-07-23
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 2468 C++ 풀이 코드 : BFS

```cpp 
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int N;
int dx[4] = { 1, 0, 0, -1 };
int dy[4] = { 0, 1, -1, 0 };
int map[101][101] = {0,};
bool isVisited[101][101] = { false, };

void BFS(int i, int j, int max) {
    pair<int, int> cur;
    pair<int, int> next;
    queue<pair<int, int>> q;
    
    q.push(make_pair(i, j));
    isVisited[i][j] = true;

    while (!q.empty()) {
        cur = q.front();
        q.pop();
        for (int i = 0; i < 4; i++) {
            next = make_pair(cur.first + dx[i], cur.second + dy[i]);
            if (0 <= next.first && next.first < N && 0 <= next.second && next.second < N) {
                if (map[next.first][next.second] > max && isVisited[next.first][next.second] == false) {
                    q.push(next);
                    isVisited[next.first][next.second] = true;
                }
            }
        }
    }
}

int main(void) {
    int cnt, max = 0;
    int max_cnt = 0;

    cin >> N;
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cin >> map[i][j];
            if (map[i][j] > max) {
                max = map[i][j];
            }
        }
    }
    for (int i = 0; i <= max; i++) {
        cnt = 0;
        for (int j = 0; j < N; j++) {
            for (int k = 0; k < N; k++) {
                isVisited[j][k] = false;
            }
        }

        for (int j = 0; j < N; j++) {
            for (int k = 0; k < N; k++) {
                if (map[j][k] > i && isVisited[j][k] == false) {
                    BFS(j, k, i);
                    cnt++;
                }
            }
        }
        if (max_cnt < cnt) {
            max_cnt = cnt;
        }
    }
    cout << max_cnt;

    return 0;
}
```

[github BOJ_2468](https://github.com/choiiis/1d-1c/blob/master/BOJ_2468.cpp)

---

## 회고

높이 입력값을 배열에 추가하면서 높이의 최대값을 max에 저장했다. 0부터 max까지 for문을 돌면서 각 조건에서 BFS로 안전 영역의 개수 구하여 cnt로 출력했다. cnt가 이전 값보다 더 커졌을 경우 max_cnt에 저장하여, 최종 max_cnt 값을 출력하여 구현하였다.