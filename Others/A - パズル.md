# A - パズル
[[Graph]] [[Union-Find]] [[ACL]] [[Black]] [[Others]]
#Graph #Union-Find #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-exhibition-open/tasks/code_festival_exhibition_a

## 解き方
### Code2
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;
pair<int, int> e[2000];
int g[2000][2000], y[2000], sum[2000];
int main() {
  int n, m; cin >> n >> m;
  REP(i, m) {
    int a, b; cin >> a >> b;
    e[i] = {--a, --b};
    g[a][b] = g[b][a] = true;
  }
  REP(i, n) cin >> y[i], y[i]--;
  dsu d(n);
  REP(i, m) {
    auto [a, b] = e[i];
    REP(j, n) if (g[a][j] && g[b][j])
      d.merge(a, b), d.merge(a, j);
  }
  REP(i, n) if (d.leader(i)!=d.leader(y[i])) return cout << "NO" << '\n', 0;
  REP(i, n) for (int j=i+1; j<n; j++)
    if(d.leader(i)==d.leader(j) && y[i]>y[j]) sum[d.leader(i)]++;
  REP(i, n) if (sum[i]%2) return cout << "NO" << '\n', 0;
  cout << "YES" << '\n';
  return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;

int main() {
  int n, m; cin >> n >> m;
  pair<int, int> edge[2000];
  bool g[2000][2000] = {};
  REP(i, m) {
    int a, b; cin >> a >> b;
    edge[i] = {--a, --b};
    g[a][b] = g[b][a] = true;
  }
  vector<int> y(n), used(n, 0), sum(n);
  REP(i, n) cin >> y[i], y[i]--;
  dsu d(n);
  REP(i, m) {
    auto [a, b] = edge[i];
    REP(j, n) if (g[a][j] && g[b][j]) {
      d.merge(a, b);
      d.merge(a, j);
    }
  }
  REP(i, n) {
    if (!used[i]) {
      int cur = i;
      int cnt = 0;
      while (!used[cur]) {
        cnt++;
        used[cur] = 1;
        if (!d.same(cur, y[cur])) {
          cout << "NO" << '\n';
          return 0;
        }
        cur = y[cur];
      }
      sum[d.leader(i)] += cnt-1;
    }
  }
  for (int x : sum) if (x%2) {
    cout << "NO" << '\n';
    return 0;
  }
  cout << "YES" << '\n';
  return 0;
}
```