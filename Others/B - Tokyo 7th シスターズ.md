# B - Tokyo 7th シスターズ
[[bit全探索]] [[popcount]] [[Light Blue]] [[Others]]
#bit全探索 #popcount #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/donuts-2015/tasks/donuts_2015_2

## 解き方
- bit 全探索と popcount で，$9$ 人の場合のみを考える．
- その $9$ 人の合計を出して，コンボ条件を満たす人が $3$ 人以上いる場合に，$9$ 人の合計にボーナスの値を足す．
- その値の最大値が答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int a[n], b[m], c[m], I[m][n];
	REP(i, n) cin >> a[i];
	REP(i, m) {
		cin >> b[i] >> c[i];
		REP(j, c[i]) cin >> I[i][j];
		REP(j, c[i]) I[i][j]--;
	}
	int res = 0;
	REP(bit, 1 << n) {
		if (__builtin_popcount(bit) != 9) continue ;
		int now = 0;
		REP(i, n) if (bit >> i & 1) now += a[i];
		REP(i, m) {
			int cnt = 0;
			REP(j, c[i]) if (bit >> I[i][j] & 1) cnt++;
			if (cnt >= 3) now += b[i];
		}
		res = max(res, now);
	}
	cout << res << '\n';
	return 0;
}
```