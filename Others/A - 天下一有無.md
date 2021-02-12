# A - 天下一有無
[[グリッド]] [[DP]] [[bit演算子]] [[Black]] [[Others]]
#グリッド #DP #bit演算子 #Black #Others 

## 問題
- https://atcoder.jp/contests/tenka1-2013-final/tasks/tenka1_2013_final_a

## 解き方

### Code3
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

int main() {
	int n, m; cin >> n >> m;
	if (n > m) swap(n, m);
	vector<int> a;
	REP(i, 1<<n) {
		bool ok = true;
		for (int j = 1; j <= i; j <<= 1) {
			if ((i&j) && (i&(j<<1))) {
				ok = false;
				break ;
			}
		}
		if (ok) a.push_back(i);
	}
	int N = a.size();
	mint dp[m+1][N];
	dp[0][0] = 1;
	REP(i, m) REP(j, N) REP(k, N)
		if (!((a[j]&a[k]) | ((a[j]<<1)&a[k]) | (a[j]&(a[k]<<1))))
			dp[i+1][k] += dp[i][j];
	mint res = 0;
	REP(i, N) res += dp[m][i];
	cout << res.val() - 1 << '\n';
	return 0;
}
```

### Code2
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

mint dp[16][1<<15];
int pat[1<<15];

int main() {
	int n, m; cin >> n >> m;
	dp[0][0] = 1;
	int t = 0;
	REP(i, 1<<m) if (!(i&i<<1)) pat[t++] = i;
	REP(i, n) REP(j, t) REP(k, t) {
		if (!(pat[j]&pat[k]) && !(pat[j]<<1&pat[k]) && !(pat[j]&pat[k]<<1))
			dp[i+1][j] += dp[i][k];
	}
	mint res = 0;
	REP(i, t) res += dp[n][i];
	cout << res.val() - 1 << '\n';
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

int main() {
	int h, w; cin >> h >> w;
	mint dp[16][1<<15] = {};
	dp[0][0] = 1;
	REP(i, h) REP(j, 1<<w) {
		int x = (1<<w)-1 & ~(j|j<<1|j>>1);
		for (int t=x; ; t=t-1&x)
			if (!(t&t<<1)) {
				dp[i+1][t] += dp[i][j];
				if (!t) break ;
			}
	}
	mint res = 0;
	REP(i, 1<<w) res += dp[h][i];
	cout << res.val() - 1 << '\n';
	return 0;
}
```