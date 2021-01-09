# C - \[\[iwi\]\]
[[DP]] [[文字列操作]] [[Black]] [[Others]]
#DP #文字列操作 #Black #Others 

## 問題
- https://atcoder.jp/contests/utpc2011/tasks/utpc2011_3

## 解き方
- DP を使って，iwi の左側の文字列と，iwi の右側の文字列の最大共通部分文字列長を探索する．
- 具体的な方法としては，
	- 右側の文字列を逆順にして，
	- 右側の文字 $1$ つ $1$ つを線対象となる文字に変換して，
	- 左側の文字と右側の文字が同じであれば，DP テーブルに $2$ を足していく．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	string str; cin >> str;
	string::size_type pos = str.find("iwi");
	string l = str.substr(0, pos);
	int nl = l.size();
	string r = str.substr(pos+3);
	int nr = r.size();
	reverse(r.begin(), r.end());
	REP(i, nr) {
		if (r[i] == '[') r[i] = ']';
		else if (r[i] == ']') r[i] = '[';
		else if (r[i] == '{') r[i] = '}';
		else if (r[i] == '}') r[i] = '{';
		else if (r[i] == '(') r[i] = ')';
		else if (r[i] == ')') r[i] = '(';
	}
	int dp[nl+1][nr+1];
	bzero(dp, sizeof(dp));
	REP(i, nl+1) REP(j, nr+1) {
		if (i < nl && j < nr)
			dp[i+1][j+1] = max(dp[i+1][j+1], dp[i][j]+((l[i]==r[j])?2:0));
		if (i < nl)
			dp[i+1][j] = max(dp[i+1][j], dp[i][j]);
		if (j < nr)
			dp[i][j+1] = max(dp[i][j+1], dp[i][j]);
	}
	cout << 3 + dp[nl][nr] << '\n';
	return 0;
}
```