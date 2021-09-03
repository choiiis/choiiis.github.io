---
title: "[Coding Challenge] BOJ 백준 2178 (미로 탐색)"
excerpt: "BOJ 백준 2178 미로 탐색 문제 코드 회고"

categories:
  - Coding Challenge
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-2178/

toc: false
 
date: 2020-06-26
last_modified_at: 2021-09-03

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# 미로 탐색
```cpp
#include <iostream>
#include <queue>

using namespace std;
int main(void) {
    int N, M;
    int maze[101][101] = { 0, };
    int count[101][101] = { 0, };
    bool isVisited[101][101] = { false, };
    int dir[4][2] = { {0, -1}, {0, 1}, {1, 0}, {-1, 0} };
    queue<pair<int, int>> q;
    cin >> N >> M;

    for (int i = 1; i <= N; i++) {
        for (int j = 1; j <= M; j++) {
            scanf("%1d", &maze[i][j]);
        }
    }

    q.push(make_pair(1, 1));
    isVisited[1][1] = true;
    count[1][1] = 1;

    while (!q.empty()) {
        pair<int, int> cur = q.front();
        q.pop();
        bool isConnected = false;
        int cur_x = cur.first;
        int cur_y = cur.second;
        for (int i = 0; i < 4; i++) {
            int next_x = cur.first + dir[i][0];
            int next_y = cur.second + dir[i][1];
            if(maze[next_x][next_y] == 1 && isVisited[next_x][next_y] == false){
                q.push(make_pair(next_x, next_y));
                isVisited[next_x][next_y] = true;
                count[next_x][next_y] = count[cur_x][cur_y] + 1;
                isConnected = true;
            }
        }
    }
    cout << count[N][M];
}
```

``회고``

공백 없이 입력하는거 쉽게 받으려면 scanf("%1d", ~) 이용하기. 한 줄에 공백 없이 여러 개 입력해도 한 숫자씩 입력 받아오는 방식이다. 경로 찾을 때 맵 따로 생성해서 현재까지의 경로의 길이를 해당 노드 위치에 넣고, 다음 위치에서 현재 위치 +1 하는 방식으로 하기.
