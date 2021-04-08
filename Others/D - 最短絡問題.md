# D - 最短絡問題
[[グリッド]] [[パターン]] [[swap]] [[Black]] [[Others]]
#グリッド #パターン #swap #Black #Others 

## 問題
- https://atcoder.jp/contests/gwcontest2015/tasks/gw2015_d

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<n; i++)
using namespace std;

int main() {
	int h, w, k; cin >> h >> w >> k;
	int v[h][w];
	REP(i, h) REP(j, w) {
		printf("1 1 %d %d\n", i+1, j+1);
		cin >> v[i][j];
	}
	while (k--) {
		int a, b, c, d; cin >> a >> b >> c >> d;
		a--, b--, c--, d--;
		if (b>d || (b==d && a<b)) {
			swap(a, c);
			swap(b, d);
		}
		if (a<=c && b<=d)
			cout << v[c][d] - v[a][b] << '\n';
		else
			cout << v[a][b] - v[c][b] - v[c][b] + v[c][d] << '\n';
	}
	return 0;
}
```