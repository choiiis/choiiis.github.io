---
title: "[Coding Challenge] BOJ 백준 7569 (토마토)"
excerpt: "BOJ 백준 7569 토마토 문제 코드 회고"

categories:
  - Coding Challenge
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-7569/

toc: false
 
date: 2020-07-25
last_modified_at: 2021-09-03

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 7569 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;
struct tomato {
    int x, y, z = 0;
};

int M, N, H;
int dx[6] = { 1, 0, 0, -1, 0, 0 };
int dy[6] = { 0, 1, -1, 0, 0, 0 };
int dz[6] = { 0, 0, 0, 0, 1, -1 };
int map[101][101][101] = {0,};
queue<tomato> q;

int BFS(void) {
    tomato cur;
    tomato next;
    int value = 0;

    while (!q.empty()) {
        cur = q.front();
        q.pop();

        for (int i = 0; i < 6; i++) {
            next = tomato({ cur.x + dx[i], cur.y + dy[i], cur.z + dz[i] });
            if (0 <= next.x && next.x < M && 0 <= next.y && next.y < N && 0 <= next.z && next.z < H) {
                if (map[next.x][next.y][next.z] == 0) {
                    q.push(next);
                    map[next.x][next.y][next.z] = map[cur.x][cur.y][cur.z] + 1;
                    value = map[next.x][next.y][next.z];
                }
            }
        }
    }
    return value - 1;
}

int main(void) {
    bool isPossible = true;
    int done = 0;
    int none = 0;
    int res;

    cin >> N >> M >> H;

    for (int i = 0; i < H; i++) {
        for (int j = 0; j < M; j++) {
            for (int k = 0; k < N; k++) {
                cin >> map[j][k][i];
                if (map[j][k][i] == 1) {
                    done++;
                    q.push(tomato({ j,k,i }));
                }
                if (map[j][k][i] == -1) {
                    none++;
                }
            }
        }
    }

    if (done + none == M * N * H) {
        if (none == M * N * H) {
            cout << -1;
        }
        else {
            cout << 0;
        }
    }
    else {
        res = BFS();

        for (int i = 0; i < H; i++) {
            for (int j = 0; j < M; j++) {
                for (int k = 0; k < N; k++) {
                    if (map[j][k][i] == 0) {
                        isPossible = false;
                    }
                }
            }
        }

        if (isPossible) {
            cout << res;
        }
        else {
            cout << -1;
        }
    }
    
    return 0;
}
```
[github BOJ_7569](https://github.com/choiiis/1d-1c/blob/master/BOJ_7569.cpp)

``회고``

3차원 배열이라서 pair 대신 구조체를 활용했다. 처음부터 익은 토마토의 좌표를 큐에 넣고 큐가 빌 때까지 BFS를 진행하면 된다. 처음에 입력값을 다 배열에 넣고 배열의 값이 1인 것에 대해서 BFS를 돌리려고 했는데, 이렇게 하면

110
000
000

이런 경우에 첫번째 1에서 전체를 다 방문해버려서 (1, 1)의 경우에는 하루면 익는데, 이틀만에 익는 것으로 나타난다. 여기서 좀 헤맸음!