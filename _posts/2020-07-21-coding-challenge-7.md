---
title: "BOJ 백준 1012 유기농 배추 (C++)"
excerpt: "BOJ 백준 1012 유기농 배추 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-1012/

toc: false
 
date: 2020-07-21
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 1012 C++ 풀이 코드 : BFS, DFS

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int T, M, N, K;
int dx[4] = { 1, 0, 0, -1 };
int dy[4] = { 0, 1, -1, 0 };

bool isVisited[51][51];
int arr[51][51];
queue<pair<int, int>> q;

void DFS(pair<int, int> cur) {
    pair<int, int> next;
    for (int i = 0; i < 4; i++) {
        next = make_pair(cur.first + dx[i], cur.second + dy[i]);
        if (0 <= next.first && next.first < M && 0 <= next.second && next.second < N) {
            if (isVisited[next.first][next.second] == false && arr[next.first][next.second] == 1) {
                isVisited[next.first][next.second] = true;
                DFS(next);
            }
        }
    }
}
int BFS(void) {
    pair<int, int> cur;
    pair<int, int> next;
    int cnt = 0;

    while (!q.empty()) {
        cur = q.front();
        q.pop();
        if (isVisited[cur.first][cur.second] == false) {
            isVisited[cur.first][cur.second] = true;
            DFS(cur);
            cnt++;
        }
    }

    return cnt;
}

int main(void) {
    int a, b;
    vector<int> ans;
    cin >> T;

    for (int i = 0; i < T; i++) {
        cin >> N >> M >> K;
        for (int k = 0; k < 51; k++) {
            for (int r = 0; r < 51; r++) {
                isVisited[k][r] = false;
                arr[k][r] = 0;
            }
        }
        for (int j = 0; j < K; j++) {
            cin >> b >> a;
            arr[a][b] = 1;
            q.push(make_pair(a, b));
        }
        ans.push_back(BFS());
    }

    for (auto i = ans.begin(); i != ans.end(); i++) {
        cout << *i << endl;
    }

    return 0;
}
```

[github BOJ_1012](https://github.com/choiiis/1d-1c/blob/master/BOJ_1012.cpp)

BFS로 풀기 : [github BOJ_1012_2](https://github.com/choiiis/1d-1c/blob/master/BOJ_1012_2.cpp)

DFS로 풀기 : [github_BOJ_1012_3](https://github.com/choiiis/1d-1c/blob/master/BOJ_1012_3.cpp)

---

## 회고

BFS와 DFS 모두 활용하기, BFS만, DFS만으로 풀기 이렇게 3가지로 구현을 해봤다. 

BFS와 DFS 모두 활용한 풀이 같은 경우에는 BFS라기 보다는 큐와 DFS를 활용했다고 할 수 있다. 먼저 배추가 들어있는 좌표의 pair 값을 큐에 모두 넣고, 큐에 있는 것을 하나씩 빼서 그 좌표부터 시작하는 DFS를 실행한다. 이 때, 방문한 위치에는 isVisited를 true로 만들어줘서 다시 방문할 경우에 넘어가도록 구현했다.

BFS만으로 구현한 풀이의 경우에는 상자 전체를 돌면서 BFS를 진행했다. 이것도 역시 방문한 노드에는 표시를 해줘서 다시 방문하지 않도록 구현하는 방식으로 했다.

DFS만으로 구현한 풀이의 경우에도 상자 전체를 돌면서 DFS를 진행했는데, 상자 전체를 도는 이중 for문을 main에 구현해서 하나의 좌표에서 시작하여 연결된 노드를 따라 깊이 우선 탐색을 진행하고 나면 cnt를 1씩 증가시켜주는 방식으로 진행했다.