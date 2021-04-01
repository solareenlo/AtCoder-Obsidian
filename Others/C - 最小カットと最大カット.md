# C - 最小カットと最大カット
[[DFS]] [[BFS]] [[DP]] [[最小カット]] [[最大カット]] [[Black]] [[Others]]
#DFS #BFS #DP #最小カット #最大カット #Black #Others 

## 問題
- https://atcoder.jp/contests/utpc2014/tasks/utpc2014_c

## 解き方
- https://physics0523.hatenablog.com/entry/2019/02/19/170852

### Code DFS
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> g[n];
	for (int i=0; i<n; i++) {
		int a, b; cin >> a >> b;
		g[--a].push_back(--b);
		g[b].push_back(a);
	}
	int l = 0;
	vector<int> dp(n, -1);
	function<void(int, int)> dfs = [&](int node, int prev) {
		if (dp[node] != -1) {
			l = dp[node] - dp[prev] + 1;
			return ;
		}
		dp[node] = dp[prev] + 1;
		for (int next : g[node]) if (next != prev)
			dfs(next, node);
	};
	dfs(0, 0);
	cout << 1+(l==n) << " " << (l%2?n-1:n) << '\n';
	return 0;
}
```

### Code BFS
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	map<int, vector<int> > g;
	for (int i=0; i<n; i++) {
		int a, b; cin >> a >> b;
		g[a].push_back(b);
		g[b].push_back(a);
	}
	queue<int> q;
	q.push(1);
	map<int, int> depth, prev;
	depth[1] = 0;
	prev[1] = -1;
	while (!q.empty()) {
		int now = q.front(); q.pop();
		for (auto &e : g[now]) if (e != prev[now]) {
			if (depth.find(e) != depth.end()) {
				int l = depth[now]+depth[e]+1;
				cout << 1+l/n << " " << n-l%2 << '\n';
				return 0;
			}
			q.push(e);
			depth[e] = depth[now]+1;
			prev[e] = now;
		}
	}
	return 0;
}
```