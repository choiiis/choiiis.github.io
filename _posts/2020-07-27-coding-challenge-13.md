---
title: "BOJ 백준 2644 촌수 계산 (C++)"
excerpt: "BOJ 백준 2644 촌수 계산 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-2644/

toc: false
 
date: 2020-07-27
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 2644 C++ 풀이 코드 : BFS

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>
#include <cstring>

using namespace std;

int n, m, start, fin;
int visit[101] = { 0, };
vector<int> v[101];

int BFS(int start) {
    queue<int> q;
    int cur;
    visit[start] = 0;
    q.push(start);

    while(!q.empty()) {
        cur = q.front();
        q.pop();
        for (auto next = v[cur].begin(); next != v[cur].end(); next++) {
            if (*next == fin) {
                return visit[cur] + 1;
            }
            if (visit[*next] == 0) {
                q.push(*next);
                visit[*next] = visit[cur] + 1;
            }
        }
    }
    return -1;
}

int main(void) {
    int a, b;
    cin >> n;
    cin >> start >> fin;
    cin >> m;
    for (int i = 0; i < m; i++) {
        cin >> a >> b;
        v[a].push_back(b);
        v[b].push_back(a);
    }
    cout << BFS(start);
    
    return 0;
}
```

[github BOJ_7569](https://github.com/choiiis/1d-1c/blob/master/BOJ_7569.cpp)

---

## 회고

vector를 활용해서 입력되는 연결 요소를 저장해놓았다. 처음 시작하는 노드부터 queue에 넣고, 하나씩 빼면서 그 노드와 연결된 노드 중 아직 방문하지 않은 노드를 queue에 넣었다. 다음 노드에 방문할 때는 이전 노드까지 계산된 촌수에 1을 더하는 방식으로 구현했다.