# E - Unique Color
[[DFS]] [[Tree]] [[Green]] [[ABC]]
#DFS #Tree #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc198/tasks/abc198_e

## 解き方
- https://blog.hamayanhamayan.com/entry/2021/04/11/225651

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=1; i<(n); i++)
using namespace std;

int c[100010], s[100010], res[100010];
vector<int> e[100010];

void dfs(int u, int p) {
	if (s[c[u]] == 0)
		res[u] = 1;
	s[c[u]]++;
	for (int x : e[u]) if (x!=p)
		dfs(x, u);
	s[c[u]]--;
}

int main() {
	int n; cin >> n;
	REP(i, n+1) cin >> c[i];
	REP(i, n) {
		int a, b; cin >> a >> b;
		e[a].push_back(b);
		e[b].push_back(a);
	}
	dfs(1, 0);
	REP(i, n+1) if (res[i])
		cout << i << '\n';
	return 0;
}
```