# D - Maximum Sum of Minimum
[[DFS]] [[BFS]] [[Tree]] [[Light Blue]] [[Others]]
#DFS #BFS #Tree #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/m-solutions2019/tasks/m_solutions2019_d


## 解き方
- 辺の score を，辺の両端の頂点 a, b の score の min(a, b) とする時，全ての辺の score の合計値をもっとも大きくするためには，スタート地点の頂点から配られた score の大きい順に並べていけば良い．
- そうすることで全ての頂点が連結になり，必ずスタート地点から遠い方の頂点の score が辺の score として採択され，辺の score の合計値が最大となる．


## Code
DFS version
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0 ; i < (n); i++)
using namespace std;

int n, score, i;
int c[10001], res[10001];
vector<int> g[10001];

void dfs(int u, int p) {
	for (int v : g[u]) {
		if (v == p) continue ;
		dfs(v, u);
	}
	res[u] = c[i++];
}

int main() {
	cin >> n;
	REP(i, n - 1) {
		int a, b; cin >> a >> b;
		g[--a].push_back(--b);
		g[b].push_back(a);
	}
	REP(i, n) {
		cin >> c[i];
		score += c[i];
	}
	sort(c, c+n);
	dfs(0, -1);
	cout << score - c[n-1] << '\n';
	REP(i, n) cout << res[i] << " ";
	return 0;
}
```

BFS version
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> g[n];
	REP(i, n - 1) {
		int a, b; cin >> a >> b;
		g[--a].push_back(--b);
		g[b].push_back(a);
	}

	vector<int> c(n);
	int score = 0;
	REP(i, n) {
		cin >> c[i];
		score += c[i];
	}
	sort(c.rbegin(), c.rend());

	queue<int> q;
	q.push(0);
	vector<int> res(n, -1);
	int i = 0;
	while (!q.empty()) {
		int now = q.front();
		q.pop();
		res[now] = c[i++];
		for (int next : g[now])
			if (res[next] == -1) q.push(next);
	}

	cout << score - c[0] << '\n';
	REP(i, n) cout << res[i] << " ";
	return 0;
}
```