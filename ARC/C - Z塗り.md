# C - Z塗り
[[パターン]] [[グリッド]] [[Light Blue]] [[ARC]]
#パターン #グリッド #Light_Blue #ARC 

## 問題
- https://atcoder.jp/contests/arc040/tasks/arc040_c

## 解き方
- まだ塗られていないマスのうち右上のものを探す ． 
- そのマスにZ字の右上の⾓角を合わせるように塗る．
-  以上を繰り返し，全部のマスが塗られるまでに繰り返した回数が答えとなる．

## Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	char s[n+1][n];
	REP(i, n) REP(j, n) cin >> s[i][j];

	int res = 0;
	REP(i, n) {
		int pos = -1;
		REP(j, n) if (s[i][j] == '.') pos = j;
		if (pos == -1) continue ;
		REP(j, pos+1) s[i][j] = 'o';
		for (int j = pos; j < n; j++) s[i+1][j] = 'o';
		res++;
	}
	cout << res << '\n';
	return 0;
}
```