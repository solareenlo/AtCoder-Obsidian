# C - Optimal Recommendations
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/indeednow-finala-open/tasks/indeednow_2015_finala_c

## 解き方
- https://www.slideshare.net/chokudai/indeednow-finala

### Code DP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int dp[101][101][101] = {};
	REP(i, n) {
		int a, b, c, w; cin >> a >> b >> c >> w;
		dp[a][b][c] = max(dp[a][b][c], w);
	}
	REP(i, 101) REP(j, 101) REP(k, 101)
		dp[i][j][k] = max(dp[i][j][k], max(dp[max(0,i-1)][j][k], max(dp[i][max(0,j-1)][k], dp[i][j][max(0,k-1)])));
	REP(i, m) {
		int x, y, z; cin >> x >> y >> z;
		cout << dp[x][y][z] << '\n';
	}
	return 0;
}
```