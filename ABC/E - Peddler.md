# E - Peddler
[[Graph]] [[DAG]] [[DP]] [[Green]] [[ABC]]
#Graph #DAG #DP #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc188/tasks/abc188_e

## 解き方
- $X_i<Y_i$ という制約のため，このグラフは DAG (Directed Acyclic Graph, 閉路を含まない有向グラフ)となる． 
- この DAG 上で以下のような DP (動的計画法) を考える．
  - $dp[i]$ : 街 $i$ に到達できる街 (街 $i$ 自身を含まない) における金の最安値
- $i$ の昇順に，$i$ から直接移動できる各街 $j$ について，$dp[j]←\min(dp[j],\ dp[i],\ Ai)$ とすればこの DP が計算できる．
- これが計算できれば，$A_i−dp[i]$ の最大値が答えとなる．
- 計算量は $O(N+M)$ となる．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int a[n];
	for (int &x : a) cin >> x;
	vector<int> G[n];
	while (m--) {
		int x, y; cin >> x >> y;
		G[--x].push_back(--y);
	}
	vector<int> dp(n, 2e9);
	int maxi = -2e9;
	for (int i = 0; i < n; i++) {
		for (int j : G[i])
			dp[j] = min(dp[j], min(dp[i], a[i]));
		if (dp[i] != 2e9)
			maxi = max(maxi, a[i] - dp[i]);
	}
	cout << maxi << '\n';
	return 0;
}
```