# B - エターナルスタティックファイナル
[[文字列操作]] [[DP]] [[Light Blue]] [[Others]]
#文字列操作 #DP #Light_Blue  #Others

## 問題
- https://atcoder.jp/contests/tenka1-2014-qualb/tasks/tenka1_2014_qualB_b


## 解き方
- 元となる文字列を1つずつインクリメントして行って，探索される文字列がそこにあれば，dp 配列をインクリメントする dp．


## Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using ll = long long;
const ll MOD = 1000000007;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	int m = size(s);
	vector<string> t(n);
	REP(i, n) cin >> t[i];

	vector<ll> dp(m + 1, 0);
	dp[0] = 1;
	REP(i, m) REP(j, n) {
		if (s.substr(i, size(t[j])) == t[j]) {
			dp[i + size(t[j])] += dp[i];
			dp[i + size(t[j])] %= MOD;
		}
	}
	cout << dp[m] << '\n';
	return 0;
}
```