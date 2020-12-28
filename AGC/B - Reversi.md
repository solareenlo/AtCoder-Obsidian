# B - Reversi
[[DP]] [[Light Blue]] [[AGC]]
#DP #Light_Blue #AGC 

## 問題
- https://atcoder.jp/contests/agc031/tasks/agc031_b

## 解き方
- $DP[i]$ を最初から $i$ 個の石たちの条件を満たすような塗り方の個数とする．
- $DP[i]$ は，$i$ 番目の石の色が $j+1$ 番目の石の色と等しく，$j$ 番目の色と異なるような $j$ たち全てに対する $DP[j]$ の和として計算できる．
	- ただし，便宜上 $0$ 番目の石の色は他のどの石の色とも違う色で塗られていると考える．
- このままでは時間計算量が $O(N^2)$ かかるので，
- 各色に対し，$j+1$ 番目の石がその色で塗られており $j$ 番目の石がその色で塗られていないような $j$ に対する $DP[j]$ の和を持っておき，
- $DP$ 値が新しく計算されるたびにその都度足し込んでいけば，各遷移を $O(1)$ 時間で解くことができ，全体として，時間計算量が $O(N)$ となる．	

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;
int64_t dp[200002];
int main() {
	int n; cin >> n;
	int res = 1, pre = -1;
	while (n--) {
		int c; cin >> c;
		if (c == pre) continue ;
		pre = c;
		dp[c] += res;
		res = dp[c] % (int)(1e9+7);
	}
	cout << res << '\n';
	return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;
const int MOD = 1e9 + 7;
int c[200002], dp[200002], sum[200002];
int main() {
	int n; cin >> n;
	REP(i, n) cin >> c[i];
	dp[0] = 1;
	REP(i, n) {
		if (c[i] != c[i-1]) (sum[c[i]] += dp[i-1]) %= MOD;
		dp[i] = sum[c[i]] % MOD;
	}
	cout << dp[n] << '\n';
	return 0;
}
```