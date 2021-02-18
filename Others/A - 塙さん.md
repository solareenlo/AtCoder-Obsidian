# A - 塙さん
[[DP]] [[ACL]] [[Black]] [[Others]]
#DP #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/tenka1-2014-final-open/tasks/tenka1_2014_final_a

## 解き方

### Code2
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

mint comb[2050][2050], dp[65][2050];

int main() {
	int h, n, w; cin >> h >> n >> w;
	comb[0][0] = 1;
	for (int i=1; i<2049; i++) REP(j, i+1)
		if (j) comb[i][j] = comb[i-1][j-1] + comb[i-1][j];
		else comb[i][j] = comb[i-1][j];
	dp[0][0] = 1;
	for (int i=1; i<=h; i++) REP(j, w+1) REP(k, n+1) if (j+k<=w) {
		if (i!=h) dp[i][j+k] += comb[j+k][k] * dp[i-1][j];
		else dp[i][j+k] += comb[j+k-1][k] * dp[i-1][j];
	}
	cout << dp[h][w].val() << '\n';
	return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

mint comb[2050][2050], dp[65][2050];

int main() {
	int h, n, w; cin >> h >> n >> w;
	REP(i, w+1) {
		comb[i][0] = comb[i][i] = 1;
		for (int j=1; j<i; j++)
			comb[i][j] = comb[i-1][j-1] + comb[i-1][j];
	}
	REP(i, min(w-1, n)+1)
		dp[1][i] = comb[w-1][i];
	for (int i=1; i<h; i++) REP(j, w+1) REP(k, n+1) {
		if (j+k>w) break ;
		dp[i+1][j+k] += dp[i][j] * comb[w-j][k];
	}
	cout << dp[h][w].val() << '\n';
	return 0;
}
```