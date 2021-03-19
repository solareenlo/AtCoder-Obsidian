# C - ドライブ
[[Union-Find]] [[DFS]] [[ACL]] [[Black]] [[Others]]
#Union-Find #DFS #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/dwango2015-honsen/tasks/dwango2015_finals_3

## 解き方
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

int main() {
	int n, m; cin >> n >> m;
	dsu d(n);
	vector<pair<int, int> > g[m+1];
	int odd[400400] = {};
	mint res = 0, fact[500500] = {};
	fact[0] = 2;
	for (int i=0; i<m; i++) {
		int a, b; cin >> a >> b;
		a--; b--;
		odd[a] ^= 1;
		odd[b] ^= 1;
		if (!d.same(a, b)) {
			d.merge(a, b);
			g[a].emplace_back(b, i);
			g[b].emplace_back(a, i);
		}
		if (i) fact[i] = fact[i-1]*2;
		res += fact[i];
	}
	function<int(int, int)> dfs = [&](int i, int par) {
		int ret = odd[i];
		for (auto e : g[i]) if (e.first != par) {
			int s = dfs(e.first, i);
			if (s%2) res += fact[e.second];
			ret += s;
		}
		return ret;
	};
	dfs(0, -1);
	cout << res.val() << '\n';
	return 0;
}
```