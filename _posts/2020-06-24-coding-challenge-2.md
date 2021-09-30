---
title: "BOJ 백준 1260 BFS, DFS (C++)"
excerpt: "BOJ 백준 1260 DFS와 BFS 문제 코드 회고"

categories:
  - 코테 / 문제해결
tags:
  - [Coding Challenge, BOJ]

permalink: /coding-challenge/boj-1260/

toc: false
 
date: 2020-06-24
last_modified_at: 2021-09-24

# sitemap :
#   changefreq : daily
#   priority : 1.0
---

# BOJ 1260 C++ 풀이 코드 : BFS, DFS

```cpp
#include <iostream>
#include <vector>
#include <stack>
#include <queue>
#include <algorithm>

using namespace std;
vector<int> v[1001];
bool isVisitedB[1001];
bool isVisitedD[1001];

void bfs(int a) {
    queue<int> q;
    
    q.push(a);
    cout << a << " ";
    isVisitedB[a] = true;
   
    while (!q.empty()) {
        int cur = q.front();
        q.pop();

        for (auto i = v[cur].begin(); i != v[cur].end(); i++) {
            if (!isVisitedB[*i]) {
                cout << *i << " ";
                isVisitedB[*i] = true;
                q.push(*i);
            }
        }
    }
    
}

void dfs(int a) {
    stack<int> s;
    s.push(a);
    isVisitedD[a] = true;
    cout << a << " ";

    while (!s.empty()) {
        bool isConnected = false;
        int cur = s.top();
        for (auto i = v[cur].begin(); i != v[cur].end(); i++) {
            if (!isVisitedD[*i]) {
                isConnected = true;
                s.push(*i);
                isVisitedD[*i] = true;
                cout << *i << " ";
                break;
            }
        }
        if (!isConnected) {
            s.pop();
        }
    }

}
int main(void) {
    int N, M, V;
    cin >> N >> M >> V;

    for (int i = 0; i < M; i++) {
        int a, b;
        cin >> a >> b;
        v[a].push_back(b);
        v[b].push_back(a);
    }

    for (int i = 0; i <= N; i++) {
        sort(v[i].begin(), v[i].end());
    }

    dfs(V);
    cout << endl;
    bfs(V);
}
```

---

## 회고

sort 쓸 때 algorithm 라이브러리 추가를 안해주면 비주얼에서는 돌아가는데 백준에서는 컴파일 에러난다. BFS, DFS 둘 다 push 할 때 isVisited 변경하고 해당 원소를 출력해야 한다. **pop에서 하지 말고 push 할 때 해야 함!**