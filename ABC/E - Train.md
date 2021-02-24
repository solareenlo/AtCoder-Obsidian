# E - Train
[[ダイクストラ法]] [[Graph]] [[Green]] [[ABC]]
#ダイクストラ法 #Graph #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc192/tasks/abc192_e

## 解き方
- ダイクストラ法で解く．
- https://blog.hamayanhamayan.com/entry/2021/02/20/233838

### Code
```c++
#include <bits/stdc++.h>
#define int int64_t
using namespace std;
using P = pair<int, int>;

signed main() {
	int n, m, x, y; cin >> n >> m >> x >> y;
	vector<tuple<int, int, int>> g[n+1];
	while (m--) {
		int u, v, t, k; cin >> u >> v >> t >> k;
		g[u].push_back({v, t, k});
		g[v].push_back({u, t, k});
	}
	priority_queue<P, vector<P>, greater<P>> q;
	vector<int> dist(n+1, 1LL<<62);
	dist[x] = 0;
	q.emplace(0, x);
	while (!q.empty()) {
		auto [du, u] = q.top(); q.pop();
		if (dist[u] < du) continue ;
		for (auto [v, t, k] : g[u]) {
			if (dist[v] > ((dist[u]+k-1)/k)*k+t) {
				dist[v] = ((dist[u]+k-1)/k)*k+t;
				q.emplace(dist[v], v);
			}
		}
	}
	cout << ((dist[y]==1LL<<62) ? -1 : dist[y]) << '\n';
    return 0;
}
```