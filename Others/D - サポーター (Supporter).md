# D - サポーター (Supporter)
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/tkppc/tasks/tkppc2015_d

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int n, r, c; cin >> n >> r >> c;
	int dp[100][100] = {};
	REP(i, r) REP(j, c) dp[i][j] = 1e9;
	dp[0][0] = 0;
	REP(i, n) REP(j, r) {
		string s; cin >> s;
		REP(k, c) if (s[k] != 'H') {
			dp[j][k] += s[k]-'0';
			if (j+1<r) dp[j+1][k] = min(dp[j+1][k], dp[j][k]);
			if (k+1<c) dp[j][k+1] = min(dp[j][k+1], dp[j][k]);
			if (i+1<n) dp[j][k] = 1e9;
		}
	}
	cout << dp[r-1][c-1] << '\n';
	return 0;
}
```