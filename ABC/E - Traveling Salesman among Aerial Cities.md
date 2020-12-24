# E - Traveling Salesman among Aerial Cities
[[DP]] [[bitDP]] [[巡回セールスマン問題]] [[Light Blue]] [[ABC]]
#DP #bitDP #巡回セールスマン問題 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc180/tasks/abc180_e

## 解き方
- 都市間の移動のコストについて三角不等式が成り立つので，ある都市から次の都市に移動するとき，別の都市を経由する必要はありません．よって各都市をちょうど1度ずつ訪問する場合についてのみ考えればよいです．

- 全ての訪問順を探索する場合 $O(N!∗N)$ 程度の時間が掛かるため，今回の制約では時間内に答えを得ることはできません．次のような DP により解くことが出来ます．

- $DP[i][S] =$ 現在地が都市 $i$ で，訪問済みの街の集合が $S$ であるときのコストの最小値
$DP[i][S] = \min{DP[j][S∖{i}]+dist(i,\ j)∣j \in S∖ {i}}$

- ここで，集合 $S$ を直接キーとして持ってもよいですが，例えば集合 ${0,\ 3,\ 5}$ を $2^0 + 2^3 + 2^5 = 41$ のように $2$ 進数に対応させることで整数として扱うことができます．そのためこのような DP は俗に bitDP とも呼ばれます．

- この対応により得られた整数を $f(S)$ とすると，$-i ∈ S ⟺  f(S)$ の $bit\ i$ が $1 - T ⊂ S ⟺ (f(T) bitwiseor f(S)) = f(S) ⟹ f(T) ≤ f(S)$  などが成り立ち，集合に関する操作・性質を bit 演算で簡潔に表現することができます．

## Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int INF = 1001001001;

int main() {
	int n; cin >> n;
	vector<int> x(n), y(n), z(n);
	REP(i, n) cin >> x[i] >> y[i] >> z[i];
	vector<vector<int> > dp(1<<n, vector<int>(n, INF));
	dp[0][0] = 0;
	REP(i, 1<<n) REP(j, n) REP(k, n) {
		int dist = abs(x[k]-x[j]) + abs(y[k]-y[j]) + max(0, z[j]-z[k]);
		dp[i|(1<<k)][k] = min(dp[i|(1<<k)][k], dp[i][j] + dist);
	}
	cout << dp[(1<<n)-1][0] << '\n';
	return 0;
}
```