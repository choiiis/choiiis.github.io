---
title: "BOJ 백준 11724 연결 요소의 개수 (C++)"
excerpt: "BOJ 백준 11724 연결 요소의 개수 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-11724/

toc: false
 
date: 2020-07-23
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 11724 C++ 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int T, M, N, K, cnt;
vector<int> map[1001] = {};
queue<int> q;
bool isVisited[1001] = { false, };

void BFS(int start) {
    q.push(start);
    isVisited[start] = true;
    while (!q.empty()) {
        int cur = q.front();
        q.pop();
        for (auto i = map[cur].begin(); i != map[cur].end(); i++) {
            if (isVisited[*i] == false) {
                q.push(*i);
                isVisited[*i] = true;
            }
        }
    }
}

int main(void) {
    int a, b, N, M;
    int cnt = 0;
    cin >> N >> M;

    for (int i = 0; i < M; i++) {
        cin >> a >> b;
        map[a].push_back(b);
        map[b].push_back(a);
    }

    for (int i = 1; i <= N; i++) {
        if (isVisited[i] == false) {
            BFS(i);
            cnt++;
        }
    }
    cout << cnt;

    return 0;
}
```

[github BOJ_11724](https://github.com/choiiis/1d-1c/blob/master/BOJ_11724.cpp)

---

## 회고

간선이 주어질 때마다 vector를 이용해서 추가해주었다. 그리고 노드를 하나씩 돌면서 BFS를 수행하고, 이미 방문한 노드의 경우에는 넘어가도록 구현하였다.