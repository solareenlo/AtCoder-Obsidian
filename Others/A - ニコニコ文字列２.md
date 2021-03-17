# A - ニコニコ文字列２
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/dwango2015-honsen/tasks/dwango2015_finals_1

## 解き方
- https://img.atcoder.jp/dwango2015-finals/editorial.pdf

### Code 2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 1e9 + 7;

int main() {
	int n, x; cin >> n >> x;
	string s; cin >> s;
	int now = 0;
	int dp[2][255][55] = {};
	dp[0][0][0] = 1;
	REP(i, n) {
		REP(j, x+1) REP(k, 51) dp[1-now][j][k] = 0;
		REP(d, 10) {
			if (s[i]!='?' && s[i]-'0'!=d) continue ;
			REP(j, x+1) REP(k, 51) {
				if (d==2)
					(dp[1-now][j][k%2?1:min(49,k+1)]+=dp[now][j][k])%=MOD;
				else if (k%2 && d==5)
					(dp[1-now][min(x,j+(k+1)/2)][min(50,k+1)]+=dp[now][j][k])%=MOD;
				else
					(dp[1-now][j][0]+=dp[now][j][k])%=MOD;
			}
		}
		now = 1-now;
	}
	int res = 0;
	REP(k, 51) (res+=dp[now][x][k])%=MOD;
	cout << res << '\n';
	return 0;
}
```

### Code 1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 1e9+7;

int main() {
	int n, x; cin >> n >> x;
	string s; cin >> s;
	vector<vector<int> > dp(n+2, vector<int>(x+1));
	dp[0][0] = 1;
	REP(i, n) {
		vector<vector<int> > dp2(n+2, vector<int>(x+1));
		REP(l, 10) {
			if (s[i]!='?' && s[i]-'0'!=l) continue ;
			for (int j=n; j>=0; j--) for (int k=x; k>=0; k--) {
				if (l==2)
					(dp2[(j%2)?1:j+1][k]+=dp[j][k])%=MOD;
				else if(l==5 && j%2)
					(dp2[j+1][min(x,k+(j+1)/2)]+=dp[j][k])%=MOD;
				else
					(dp2[0][k]+=dp[j][k])%=MOD;
			}
		}
		dp.swap(dp2);
	}
	int res = 0;
	REP(i, n+1) (res+=dp[i][x])%=MOD;
	cout << res << '\n';
	return 0;
}
```