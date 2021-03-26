# F - 就職活動
[[DP]] [[組合せ]] [[全探索]] [[Hall's Theorem]] [[Graph]] [[mincut]] [[MOD]] [[ACL]][[Black]] [[Others]]
#DP #組合せ #全探索 #Graph #mincut #MOD #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/indeednow-finala-open/tasks/indeednow_2015_finala_f

## 解き方
- https://www.slideshare.net/chokudai/indeednow-finala

## Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

mint co[151][151], dp[151][301][301];

int main() {
	int n, S, N, K; cin >> n >> S >> N >> K;
	if (S+N+K < n) { cout << 0 << '\n'; return 0; }
	REP(i, 151) {
		co[i][0] = co[i][i] = 1;
		for (int j=1; j<i; j++)
			co[i][j] = co[i-1][j]+co[i-1][j-1];
	}
	REP(i, n+1) REP(j, n+1) REP(k, n+1) if (i+j+k <= n) {
		dp[i+j+k][i][j] = co[i+j+k][i]*co[j+k][j];
	}
	REP(i, 151) REP(j, 301) REP(k, 301) {
		if (j>0) dp[i][j][k] += dp[i][j-1][k];
		if (k>0) dp[i][j][k] += dp[i][j][k-1];
		if (j>0 && k>0) dp[i][j][k] -= dp[i][j-1][k-1];
	}
	mint res = 0;
	REP(i, S+1)
		REP(j, N+1) if (i+j<=n)
		REP(k, K+1) if (i+j+k<=n)
		REP(sn, S+N-i-j+1) if (i+j+k+sn<=n) {
			res += co[n][i]*co[n-i][j]*co[n-i-j][k]*co[n-i-j-k][sn]*dp[n-i-j-k-sn][N+K-j-k][K+S-k-i];
	}
	cout << res.val() << '\n';
	return 0;
}
```