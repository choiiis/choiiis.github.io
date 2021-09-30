---
title: "BOJ 백준 7562 나이트의 이동 (C++)"
excerpt: "BOJ 백준 7562 나이트의 이동 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-7562/

toc: false
 
date: 2020-07-25
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 7562 C++ 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>
#include <cstring>

using namespace std;

int dx[8] = { 2, 1, -2, -1, 1, 2, -2, -1 };
int dy[8] = { 1, 2, 1, 2, -2, -1, -1, -2 };
int map[300][300];
int visit[300][300];

void BFS(int l, pair<int, int> start, pair<int, int> fin) {
    int count = 0;
    queue<pair<int, int>> q;
    pair<int, int> cur;
    pair<int, int> next;
    q.push(start);
    visit[start.first][start.second] = 0;

    while (!q.empty()) {
        cur = q.front();
        q.pop();
        for (int i = 0; i < 8; i++) {
            next = make_pair(cur.first + dx[i], cur.second + dy[i]);
            if (0 <= next.first && next.first < l && 0 <= next.second && next.second < l) {
                if (visit[next.first][next.second] == -1) {
                    q.push(next);
                    visit[next.first][next.second] = visit[cur.first][cur.second] + 1;
                    if (next.first == fin.first && next.second == fin.second) {
                        return;
                    }
                }
            }
        }
    }
}

int main(void) {
    int N, l;
    vector<int> v;
    cin >> N;
    for (int i = 0; i < N; i++) {
        memset(map, 0, sizeof(map));
        memset(visit, -1, sizeof(visit));
        pair<int, int> start;
        pair<int, int> fin;
        cin >> l;
        cin >> start.first >> start.second;
        cin >> fin.first >> fin.second;
        if (start.first == fin.first && start.second == fin.second) {
            v.push_back(0);
        }
        else {
            BFS(l, start, fin);
            v.push_back(visit[fin.first][fin.second]);
        }
    }
    for (auto i = v.begin(); i != v.end(); i++) {
        cout << *i << endl;
    }
    return 0;
}
```

[github BOJ_7562](https://github.com/choiiis/1d-1c/blob/master/BOJ_7562.cpp)

---

## 회고

dx와 dy 행렬의 원소만 좀 차이가 있을 뿐 이전의 BFS 문제들과 비슷했다. 차이가 있다면, start와 fin이 일치할 경우 BFS를 끝나게 하는 것을 구현해야 하는 것과 테스트 케이스마다 행렬들을 초기화 해주어야 한다는 점이다.