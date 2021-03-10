# F - 太鼓ゲーム
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/code-thanks-festival-2014-b-open/tasks/code_thanks_festival_14_qualb_f

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

const int MOD = 1e9 + 7;
int dp[1001];

int main() {
	string x, s, t; cin >> x >> s >> t;
	dp[0] = 1;
	for (int i=0; i<(int)x.size(); i++) {
		if (x.substr(i, s.size()) == s)
			(dp[i+s.size()] += dp[i]) %= MOD;
		if (x.substr(i, t.size()) == t)
			(dp[i+t.size()] += dp[i]) %= MOD;
	}
	cout << dp[x.size()] << '\n';
	return 0;
}
```