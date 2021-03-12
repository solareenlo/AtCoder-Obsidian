# C - 文字列の書き換え
[[文字列操作]] [[DP]] [[Black]] [[Others]]
#文字列操作 #DP #Black #Others 

## 問題
- https://atcoder.jp/contests/NYC2015/tasks/nyc2015_3

## 解き方
### Code DP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	string s, t; cin >> s >> t;
	int ns = s.size();
	int nt = t.size();
	bool dp[5001][5001] = {};// dp[i][j] = (s[0,i) から t[0,j) が作れるか)
	dp[0][0] = 1;
	REP(i, ns) REP(j, nt) if (dp[i][j] && s[i]==t[j]) {
		dp[i+1][j+1] = 1;
		if (j<nt-1 && s[i]!=t[j+1])
			for (j++; j<=nt; j++)
				dp[i+1][j] = 1;
	}
	cout << (dp[ns][nt] ? "Yes" : "No") << '\n';
	return 0;
}
```
Reference: https://atcoder.jp/contests/NYC2015/submissions/19237847

### Code 文字列操作
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s, t; cin >> s >> t;
	int i, j = 0;
	for (i=0; i<=(int)t.size(); i++)
		if(t[i]==s[j])
			j++;
	if (s[0]!=t[0] || j<(int)s.size()) {
		cout << "No" << '\n';
		return 0;
	}
	for (i=1; i<(int)s.size() && s[i]==s[0]; i++);
	for (j=1; j<(int)t.size() && t[j]==t[0]; j++);
	cout << ((i<j) ? "No" : "Yes") << '\n';
	return 0;
}
```
Reference: https://atcoder.jp/contests/NYC2015/submissions/2290231