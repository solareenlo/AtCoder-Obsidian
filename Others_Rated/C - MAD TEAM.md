# C - MAD TEAM
[[二分探索]] [[DP]] [[Light Blue]] [[Others]]
#二分探索 #DP #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/zone2021/tasks/zone2021_c

## 解き方
- https://atcoder.jp/contests/zone2021/editorial/1197

### Code 二分探索
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n][5];
	REP(i, n) REP(j, 5) cin >> a[i][j];
	int l = 0, r = 1e9+1;
	while (r-l > 1) {
		int m = (l+r)/2;
		set<int> s;
		REP(i, n) {
			int x = 0;
			REP(j, 5) if (a[i][j] >= m)
				x |= 1<<j;
			s.insert(x);
		}
		int x = 0;
		for (int i : s) for (int j : s) for (int k : s)
			x = max(x, i | j | k);
		(x==31?l:r) = m;
	}
	cout << l << '\n';
	return 0;
}
```

### Code DP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector dp(4, vector(1<<5, 0));
	dp[0][0] = 1e9;
	while (n--) {
		auto dp2 = dp;
		REP(i, 5) {
			int a; cin >> a;
			REP(j, 3) REP(k, 1<<5) if (k&1<<i)
				dp2[j][k] = max(dp2[j][k], min(dp2[j][k^1<<i], a));
		}
		REP(j, 3) REP(k, 1<<5)
			dp[j+1][k] = max(dp[j+1][k], dp2[j][k]);
	}
	cout << dp[3][(1<<5)-1] << '\n';
	return 0;
}
```