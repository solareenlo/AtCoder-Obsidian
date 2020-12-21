# C - 身体バランス
[[ダイクストラ法]] [[2点間の最短距離]] [[Light Blue]] [[Others]]
#ダイクストラ法 #2点間の最短距離 #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-morning-easy/tasks/code_festival_morning_easy_c

## 解き方
- 全部の2点間の最短距離を計算して，
- `スタート地点から途中までの距離 = 途中からゴールまでの距離` の場所が答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;

int main() {
	int n, m, s, t; cin >> n >> m >> s >> t;
	vector<vector<int> > d(n+1, vector<int>(n+1, 1e6));
	REP(i, m) {
		int x, y, dist; cin >> x >> y >> dist;
		d[x][y] = d[y][x] = dist;
	}
	REP(k, n) REP(i, n) REP(j, n)
		d[i][j] = min(d[i][j], d[i][k]+d[k][j]);
	int res = -1;
	REP(i, n)
		if (d[s][i]!=1e6 && d[s][i]==d[i][t])
			res = i;
	cout << res << '\n';
	return 0;
}
```