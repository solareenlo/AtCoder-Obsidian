# B - ヘイホー君と削除
[[文字列操作]] [[DP]] [[Light Blue]] [[Others]]
#文字列操作 #DP #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2015-morning-middle/tasks/cf_2015_morning_easy_d

## 解き方
- 文字列を前半部分と後半部分に分けて，同じ順番で同じ文字の組み合わせが何個あるのかを DP を用いて計算し，その時の同じ文字の組み合わせの最大値の $2$ 倍を $N$ から引いたものが答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	int maxi = 0;
	REP(k, n+1) {
		string l = s.substr(0, k);
		string r = s.substr(k);
		int L = l.size();
		int R = r.size();
		int dp[100][100] = {};
		REP(i, L) REP(j, R) {
			if (l[i]==r[j]) dp[i+1][j+1] = dp[i][j]+1;
			else dp[i+1][j+1] = max(dp[i+1][j], dp[i][j+1]);
		}
		maxi = max(maxi, dp[L][R]);
	}
	cout << n-maxi*2 << '\n';
	return 0;
}
```