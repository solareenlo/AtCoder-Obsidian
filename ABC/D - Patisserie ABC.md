# D - Patisserie ABC
[[全探索]] [[bit全探索]] [[Light Blue]] [[ABC]]
#全探索 #bit全探索 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc100/tasks/abc100_d

## 解き方
- 綺麗さの合計の絶対値，美味しさの合計の絶対値，人気度の合計の絶対値，の $3$ つの絶対値の合計の最大値なので，$2^3$ 個のパターンを全探索する．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int64_t a[n][3];
	REP(i, n) REP(j, 3) cin >> a[i][j];
	int64_t res = -1e16;
	REP(bit, 8) {
		int64_t vec[n];
		bzero(vec, sizeof(vec));
		REP(i, n) REP(j, 3)
			vec[i] += ((bit>>j)&1) ? a[i][j] : -a[i][j];
		sort(vec, vec+n, greater<int64_t>());
		int64_t sum = 0;
		REP(i, m) sum += vec[i];
		res = max(res, sum);
	}
	cout << res << '\n';
	return 0;
}
```