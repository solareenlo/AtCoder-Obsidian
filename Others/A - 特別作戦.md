# A - 特別作戦
[[DP]] [[bit演算子]] [[Black]] [[Others]]
#DP #bit演算子 #Black #Others 

## 問題
- https://atcoder.jp/contests/maximum-cup-2013/tasks/maximum_2013_a

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0 ; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	if (n == 2) {
		cout << "0 0" << '\n';
		return 0;
	}

	int g[15][15] = {};
	REP(i, n-1) for (int j = i+1; j < n; j++) {
		cin >> g[i][j];
		g[j][i] = g[i][j];
	}

	int dp[1<<15][15];
	REP(i, 1<<15) REP(j, n) dp[i][j] = 1e9;
	dp[1][0] = 0;
	for (int i=1; i<1<<n; i++) REP(j, n) REP(k, n) if ((~i>>k)&1)
		dp[i|1<<k][k] = min(dp[i|1<<k][k], dp[i][j]+g[j][k]);

	int res = 1e9;
	REP(i, n) res = min(res, dp[(1<<n)-1][i]+g[i][0]);
	cout << n << " " << res << '\n';
	return 0;
}
```