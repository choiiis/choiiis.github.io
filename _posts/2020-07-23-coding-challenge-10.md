---
title: "[Coding Challenge] BOJ 백준 2583 (영역 구하기)"
excerpt: "BOJ 백준 2583 영역 구하기 문제 코드 회고"

categories:
  - Coding Challenge
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-2583/

toc: false
 
date: 2020-07-23
last_modified_at: 2021-09-03

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 2583 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;

int N, M;
int dx[4] = { 1, 0, 0, -1 };
int dy[4] = { 0, 1, -1, 0 };
int map[101][101] = {0,};
bool isVisited[101][101] = { false, };

int BFS(int i, int j) {
    int cnt = 0;
    pair<int, int> cur;
    pair<int, int> next;
    queue<pair<int, int>> q;

    q.push(make_pair(i, j));
    isVisited[i][j] = true;
    cnt++;

    while (!q.empty()) {
        cur = q.front();
        q.pop();
        for (int i = 0; i < 4; i++) {
            next = make_pair(cur.first + dx[i], cur.second + dy[i]);
            if (0 <= next.first && next.first < N && 0 <= next.second && next.second < M) {
                if (isVisited[next.first][next.second] == false && map[next.first][next.second] == 0) {
                    q.push(next);
                    isVisited[next.first][next.second] = true;
                    cnt++;
                }
            }
        }
    }

    return cnt;
}

int main(void) {
    int K;
    int x1, y1, x2, y2;
    vector<int> res;

    cin >> N >> M >> K;

    for (int i = 0; i < K; i++) {
        cin >> x1 >> y1 >> x2 >> y2;
        for (int j = min(x1, x2); j < max(x1, x2); j++) {
            for (int k = min(y1, y2); k < max(y1, y2); k++) {
                map[k][j] = 1;
                isVisited[k][j] = false;
            }
        }
    }


    for (int i = 0; i < N; i++) {
        for (int j = 0; j < M; j++) {
            if (map[i][j] == 0 && isVisited[i][j] == false) {
                res.push_back(BFS(i, j));
            }
        }
    }
    sort(res.begin(), res.end());

    cout << res.size() << endl;
    for (auto i = res.begin(); i != res.end(); i++) {
        cout << *i << " ";
    }

    return 0;
}
```
[github BOJ_2583](https://github.com/choiiis/1d-1c/blob/master/BOJ_2583.cpp)

``회고``

두 점이 주어졌을 때 두 점 사이의 배열 map의 값을 1로 입력한다. 모두 입력이 된 상태가 되면, 배열 전체를 돌면서 map의 값이 0이고 아직 방문하지 않은 노드를 시작으로 BFS를 진행하여 인접한 영역을 모두 방문하도록 한다. 이 때 방문할 때마다 cnt를 1씩 키워주어 방문한 영역의 수를 구하여 return한다. return한 값들은 모두 vector에 저장하여 vector의 size를 구하고, 저장되어 있는 값을 출력한다.