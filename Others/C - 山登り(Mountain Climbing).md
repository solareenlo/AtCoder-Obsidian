# C - 山登り(Mountain Climbing)
[[Tree]] [[DFS]] [[Black]] [[Others]]
#Tree #DFS #Black #Others 

## 問題
- https://atcoder.jp/contests/k4pc/tasks/k4pc_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

const int N = 1e5+3;
vector<int> G[N];
multiset<int> S;
int dis[N];
bool visited[N];

void dfs(int i) {
  if (visited[i]) return ;
  visited[i] = true;
  if (!G[i].size()) S.erase(S.find(dis[i]));
  for (int j=0; j<(int)G[i].size(); j++) dfs(G[i][j]);
}

int main() {
  int n, m; cin >> n >> m;
  for (int i=2; i<=n; i++) {
    int p, w; cin >> p >> w;
    G[p].push_back(i);
    dis[i] = dis[p] + w;
  }
  for (int i=1; i<=n; i++)
    if (!G[i].size()) S.insert(dis[i]);
  while (m--) {
    int x; cin >> x;
    dfs(x);
    cout << ((!S.size()) ? -1 : *S.begin()) << '\n';
  }
  return 0;
}
```