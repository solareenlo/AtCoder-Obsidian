# D - 三角パズル
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/wupc2012/tasks/wupc2012_4

## 解き方
- 上から順に DP するか，下から順に DP するか．
- 今回は DP テーブル使わずにそのままデータの上書きで解ける．

### Code2
上から順に DP した場合．
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n][n];
	bzero(a, sizeof(a));
	REP(i, n) REP(j, i+1) cin >> a[i][j];
	REP(i, n) REP(j, n) {
		if (i > 0 && j > 0)
			a[i][j] = max(a[i][j] + a[i-1][j], a[i][j] + a[i-1][j-1]);
		else if (i > 0)
			a[i][j] += a[i-1][j];
	}
	int res = 0;
	REP(i, n) res = max(res, a[n-1][i]);
	cout << res << '\n';
	return 0;
}
```

### Code1
下から順に DP した場合．
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[101][101] = {0};
	REP(i, n) REP(j, i+1) cin >> a[i][j];
	for (int i = n-2; i >= 0; i--) REP(j, i+1)
		a[i][j] = max(a[i][j]+a[i+1][j], a[i][j]+a[i+1][j+1]);
	cout << a[0][0] << '\n';
	return 0;
}
```