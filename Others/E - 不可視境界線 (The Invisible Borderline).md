# E - 不可視境界線 (The Invisible Borderline)
[[DFS]] [[struct]] [[Black]] [[Others]]
#DFS #struct #Black #Others 

## 問題
- https://atcoder.jp/contests/tkppc/tasks/tkppc2015_e

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

struct edge {
	int to;
	int cost;
};
int64_t dist[2][100001];
vector<edge> g[100001];

void dfs(int pos, int pre, int id) {
	for (edge e : g[pos]) {
		if (e.to != pre) {
			dist[id][e.to] = dist[id][pos] + e.cost;
			dfs(e.to, pos, id);
		}
	}
}

int main() {
	int n; cin >> n;
	REP(i, n-1) {
		int a, b, c; cin >> a >> b >> c;
		g[--a].push_back(edge({--b, c}));
		g[b].push_back(edge({a, c}));
	}
	dfs(0, -1, 0);
	int p1 = max_element(dist[0], dist[0]+n) - dist[0];
	dfs(p1, -1, 1);
	int p2 = max_element(dist[1], dist[1]+n) - dist[1];
	dist[0][p2] = 0;
	dfs(p2, -1, 0);
	REP(i, n) {
		if (dist[0][i] != dist[1][i])
			cout << (dist[0][i]>dist[1][i]?p2:p1)+1 << '\n';
		else
			cout << min(p1, p2)+1 << '\n';
	}
	return 0;
}
```