# F - ループを探せ
[[Graph]] [[Loop]] [[DFS]] [[BFS]] [[Black]] [[Others]]
#Graph #Loop #DFS #BFS #Black #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-relay/tasks/code_festival_relay_f

## 解き方

### Code BFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
  int n; cin >> n;
  vector<vector<int> > g(n);
  vector<int> cnt(n, 0);
  REP(i, n) {
    int x, y; cin >> x >> y;
    g[--x].push_back(--y);
    g[y].push_back(x);
    cnt[x]++;
    cnt[y]++;
  }
  queue<int> q;
  REP(i, n) if (cnt[i] == 1)
    q.push(i);
  int res = n;
  while (!q.empty()) {
    int u = q.front(); q.pop();
    for (auto e : g[u]) {
      cnt[e]--;
      if (cnt[e] == 1)
        q.emplace(e);
    }
    res--;
  }
  cout << res << '\n';
  return 0;
}
```

### Code DFS
```c++
#include <bits/stdc++.h>
using namespace std;

vector<int> g[100001];
int d[100001];

int dfs(int u, int p, int D) {
  d[u] = D;
  for (int e : g[u]) {
    if (e == p) continue;
    if (d[e]) return D - d[e] + 1;
    else {
      int x = dfs(e, u, D + 1);
      if (x) return x;
    }
  }
  return 0;
}

int main() {
  int n; cin >> n;
  while (n--) {
    int x, y; cin >> x >> y;
    g[x].push_back(y);
    g[y].push_back(x);
  }
  cout << dfs(1, 0, 1) << '\n';
  return 0;
}
```