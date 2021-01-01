# C - 正直者の高橋くん
[[Graph]] [[最短経路]] [[DAG]] [[DP]] [[Light Blue]] [[ABC]]
#Graph #最短経路 #DAG #DP #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc021/tasks/abc021_c

## 解き方
- 頂点 $a$ から全ての頂点への最短経路 DAG を構築する途中で，頂点 $a$ から頂点 $b$ への経路の個数が見つかったらそれが答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a, b; cin >> a >> b; a--; b--;
	int m; cin >> m;
	vector<int> d[n];
	REP(i, m) {
		int x, y; cin >> x >> y; x--; y--;
		d[x].push_back(y);
		d[y].push_back(x);
	}
	int dp[n+1][n];
	memset(dp, 0, sizeof(dp));
	dp[0][a] = 1;
	REP(i, n) REP(j, n) {
		if (dp[i][j] == 0) continue ;
		if (j == b) {
			cout << dp[i][j] << '\n';
			return 0;
		}
		REP(k, (int)(d[j].size())) {
			int to = d[j][k];
			(dp[i+1][to] += dp[i][j]) %= (int)(1e9+7);
		}
	}
    return 0;
}
```