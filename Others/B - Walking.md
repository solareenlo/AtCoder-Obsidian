# B - Walking
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/pakencamp-2020-day2/tasks/pakencamp_2020_day2_b

## 解き方
- 以下のような DP を考える．
- $DP[i][j] = (i,\ j)\text{に到達するのに必要な回数}$
- $C[i][j] = `S`$ の時
	- $DP[i+1][j]$ ← $DP[i][j]$
	- $DP[i][j+1]$ ← $DP[i][j] + 1$
- $C[i][j] = `E`$ の時	
	- $DP[i][j+1]$ ← $DP[i][j]$
	- $DP[i+1][j]$ ← $DP[i][j]+1$
	
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int h, w; cin >> h >> w;
	string s[h];
	REP(i, h) cin >> s[i];
	int dp[h+1][w+1];
	REP(i, h+1) REP(j, w+1) dp[i][j] = 1e9;
	dp[0][0] = 0;
	REP(i, h) REP(j, w) {
		dp[i+1][j] = min(dp[i+1][j], dp[i][j] + (s[i][j] != 'S'));
		dp[i][j+1] = min(dp[i][j+1], dp[i][j] + (s[i][j] != 'E'));
	}
	cout << dp[h-1][w] << '\n';
	return 0;
}
```