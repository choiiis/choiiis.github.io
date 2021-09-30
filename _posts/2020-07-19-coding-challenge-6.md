---
title: "BOJ 백준 7576 토마토 (C++)"
excerpt: "BOJ 백준 7576 토마토 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-7576/

toc: false
 
date: 2020-07-19
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 7576 C++ 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int M, N;
int dx[4] = { 1, 0, 0, -1 };
int dy[4] = { 0, 1, -1, 0 };

int box[1001][1001] = { 0, };
queue<pair<int, int>> q;

int BFS(void) {
    bool isDone = false;
    pair<int, int> cur;
    pair<int, int> next;

    while (!q.empty()) {
        cur = q.front();
        q.pop();
        for (int i = 0; i < 4; i++) {
            next = make_pair(cur.first + dx[i], cur.second + dy[i]);
            if (0 <= next.first && next.first < M && 0 <= next.second && next.second < N) {
                if (box[next.first][next.second] == 0) {
                    q.push(make_pair(next.first, next.second));
                    box[next.first][next.second] = box[cur.first][cur.second] + 1;
                }
            }
        }
    }
    
    for (int i = 0; i < M; i++) {
        for (int j = 0; j < N; j++) {
            if (box[i][j] == 0) {
                isDone = true;
            }
        }
    }

    if (!isDone) {
        return box[cur.first][cur.second] - 1;
    }
    else {
        return -1;
    }
}

int main(void) {
    int tmp, res = 0;
    int none = 0;
    
    cin >> N >> M;

    for (int i = 0; i < M; i++) {
        for (int j = 0; j < N; j++) {
            cin >> tmp;
            if (tmp == 1) {
                q.push(make_pair(i, j));
            }
            else if (tmp == -1) {
                none++;
            }
            box[i][j] = tmp;
        }
    }
    if (q.size() + none == M * N) {
        cout << 0;
    }
    else {
        cout << BFS();
    }
    return 0;
}
```

[github BOJ_7576](https://github.com/choiiis/1d-1c/blob/master/BOJ_7576.cpp)

---

## 회고

먼저 익은 토마토가 들어있는 칸을 큐에 넣고, 비어있는 칸의 개수를 구했다. 익은 토마토와 비어있는 칸으로 M*N 칸이 모두 채워진 경우 0을 바로 출력하고, 아닌 경우에 BFS 함수를 호출하여 며칠이 지나야 다 익는지를 계산했다. BFS를 진행하면서 배열에 방문한 날짜를 기록하고, 마지막까지 0인 칸이 없으면 마지막 방문한 노드의 배열 값을 리턴했다. 0인 칸이 남아있을 경우 -1을 리턴.