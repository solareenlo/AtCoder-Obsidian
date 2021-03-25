# D - Longest Path
[[DFS]] [[Tree]] [[Black]] [[Others]]
#DFS #Tree #Black #Others 

## 問題
- https://atcoder.jp/contests/indeednow-finala-open/tasks/indeednow_2015_finala_d

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

struct edge{ int to, flag; };
vector<edge> G[100001];
int res, A[100001], B[100001];

void dfs(int pos, int prev) {
	for (auto e : G[pos]) if (e.to != prev) {
		dfs(e.to, pos);
		if (e.flag != 2)
			res = max(res, A[e.to]+1+B[pos]);
		if (e.flag != 1)
			res = max(res, A[pos]+B[e.to]+1);
		if (e.flag != 2)
			A[pos] = max(A[pos], A[e.to]+1);
		if (e.flag != 1)
			B[pos] = max(B[pos], B[e.to]+1);
	}
}

int main() {
	int n; cin >> n;
	for (int i=0; i<n-1; i++) {
		int a, b, c; cin >> a >> b >> c;
		G[a].push_back((edge){b,c==2?0:1});
		G[b].push_back((edge){a,c==2?0:2});
	}
	dfs(1, -1);
	cout << res-1 << '\n';
	return 0;
}
```