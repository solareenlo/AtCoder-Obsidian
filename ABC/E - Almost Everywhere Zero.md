# E - Almost Everywhere Zero
[[DP]] [[桁DP]] [[Light Blue]] [[ABC]]
#DP #桁DP #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc154/tasks/abc154_e

## 解き方
- 桁 DP と呼ばれる考え方で解ける．
- $dp[i][0][k] =$ 上から $i$ 桁目まで決めて，$0$ でない桁が $k$ 個あり，$N$ より小さいことが確定している．
- $dp[i][1][k] =$ 上から $i$ 桁目まで決めて，$0$ でない桁が $k$ 個あり，$N$ より小さいことが確定していない．
- として，$i$ が小さい方から順に計算していく．
- 答えは，$N$ の桁数を $n$ とすると，$dp[n][0][K] + dp[n][1][K]$．
- 計算時間量は $O(nK)$．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	string str; cin >> str;
	int n = str.size();
	int K; cin >> K;

	int dp[n+1][2][K+1];
	memset(dp, 0, sizeof(dp));

	dp[0][0][0] = 1;
	REP(i, n) REP(j, 2) {
		int r = j ? 9 : str[i]-'0';
		REP(k, K+1) REP(l, r+1) {
			int c = k + !!l;
			if (c <= K)
				dp[i+1][j||l<r][c] += dp[i][j][k];
		}
	}
	cout << dp[n][0][K] + dp[n][1][K] << '\n';
	return 0;
}
```