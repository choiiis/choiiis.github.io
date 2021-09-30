---
title: "BOJ 백준 2667 단지 번호 붙이기 (C++)"
excerpt: "BOJ 백준 2667 단지 번호 붙이기 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-2667/

toc: false
 
date: 2020-06-26
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 2667 C++ 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <stack>
#include <algorithm>

using namespace std;

vector<vector<int>> map;
vector<vector<bool>> isVisited;
int dir[4][2] = { {0, -1}, {0, 1}, {1, 0}, {-1, 0} };


int bfs(pair<int, int> init_pair) {
    queue<pair<int, int>> q;
    int count = 1;
    pair<int, int> cur = init_pair;
    isVisited[cur.first][cur.second] = true;
    q.push(init_pair);

    while (!q.empty()) {
        pair<int, int> cur = q.front();
        q.pop();
        for (int i = 0; i < 4; i++) {
            pair<int, int> next = make_pair(cur.first + dir[i][0], cur.second + dir[i][1]);
            if (isVisited[next.first][next.second] == false && map[next.first][next.second] == 1) {
                isVisited[next.first][next.second] = true;
                count += 1;
                q.push(make_pair(next.first, next.second));
            }
        }    
    }

    return count;
    
}


int dfs(pair<int, int> init_pair) {
    stack<pair<int, int>> q;
    int count = 1;
    pair<int, int> cur = init_pair;
    isVisited[cur.first][cur.second] = true;
    q.push(init_pair);

    while (!q.empty()) {
        pair<int, int> cur = q.top();
        bool isConnected = false;
        //q.pop();
        for (int i = 0; i < 4; i++) {
            pair<int, int> next = make_pair(cur.first + dir[i][0], cur.second + dir[i][1]);
            if (isVisited[next.first][next.second] == false && map[next.first][next.second] == 1) {
                isVisited[next.first][next.second] = true;
                count += 1;
                q.push(make_pair(next.first, next.second));
                isConnected = true;
                break;
            }
        }
        if (isConnected == false) {
            q.pop();
        }
    }

    return count;
}

int main(void) {
    int N, tmp;
    vector<int> complex;
    cin >> N;
    map.assign(N + 2, vector<int>(N + 2,0));
    isVisited.assign(N + 2, vector<bool>(N + 2, false));

    for (int i = 1; i <= N; i++) {
        for (int j = 1; j <= N; j++) {
            scanf("%1d", &map[i][j]);
        }
    }

    for (int i = 1; i <= N; i++) {
        for (int j = 1; j <= N; j++) {
            if (map[i][j] == 1 && isVisited[i][j] == 0) {
                int complex_num = dfs(make_pair(i, j));
                complex.push_back(complex_num);
            }
        }
    }

    cout << complex.size() << endl;
    sort(complex.begin(), complex.end());
    for (auto i = complex.begin(); i != complex.end(); i++) {
        cout << *i << endl;
    }
}
```

---

## 회고

dfs나 bfs나 속도 차이는 크게 없었다. 경로가 아니라 탐색 자체가 포인트이기 때문에 경로 배열 만들어 줄 필요 없고, 그냥 탐색하는 노드 수를 세도록 구현했다.
