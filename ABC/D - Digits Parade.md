# D - Digits Parade
[[数学的考察考察]] [[DP]] [[Light Blue]] [[ABC]]
#数学的考察 #DP #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc135/tasks/abc135_d

## 解き方
- 次の漸化式を考える．
$$
dp[i][j] := \text{先頭}\ i\ \text{文字として考えられるもののうち，}\ 13\  \text{で割ったあまりが}\ j\ \text{であるものの数}
$$
- このとき $i$ の昇順に $dp$ テーブルを見ると，$i − 1$ 文字目までを $13$ で割ったあまり $(dp[i − 1][j]\ \text{の}\ j)$ と $s[i]$ としてあり得る数字を全て試すことで $dp[i][0] ∼ dp[i][12]$ の値がわかる．

### Code1
```c++
#include <iostream>
#include <strings.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 1e9+7;
int main() {
	string s; cin >> s;
	int n = s.size();
	int dp[n+1][13];
	bzero(dp, sizeof(dp));
	dp[0][0] = 1;
	REP(i, n) REP(j, 13) {
		if (s[i] == '?')
			REP(k, 10)
				(dp[i+1][(j*10+k)%13] += dp[i][j]) %= MOD;
		else
			(dp[i+1][(j*10+s[i]-'0')%13] += dp[i][j]) %= MOD;
	}
	cout << dp[n][5] << '\n';
	return 0;
}
```

### Code2
```c++
#include <iostream>
#include <string.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 1e9+7;
int main() {
	string s; cin >> s;
	int dp[13] = {0};
	dp[0] = 1;
	REP(k, (int)s.size()) {
		int v[13] = {};
		REP(i, 13) {
			if (s[k] == '?')
				REP(j, 10) (v[(i*10+j)%13] += dp[i]) %= MOD;
			else
				(v[(i*10+s[k]-'0')%13] += dp[i]) %= MOD;
		}
		memmove(dp, v, sizeof(dp));
	}
	cout << dp[5] << '\n';
	return 0;
}
```