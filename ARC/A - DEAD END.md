# A - DEAD END
[[グリッド]] [[上下左右4方向]] [[パターン]] [[Gray]] [[ARC]]
#グリッド #上下左右4方向 #パターン #Gray #ARC 

## 問題
- https://atcoder.jp/contests/arc021/tasks/arc021_1

## 解き方
- 上下左右に同じ数字があるかないかを全探索．
- 同じ数字が $1$ つでもあれば "CONTINUE"．
- 同じ数字がなければ "GAMEOVER"．

### Code2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int a[5][5];
int main() {
	REP(i, 4) REP(j, 4) {
		cin >> a[i][j];
		if (a[i][j] == a[i-1][j] || a[i][j] == a[i][j-1]) {
			cout << "CONTINUE" << '\n';
			return 0;
		}
	}
	cout << "GAMEOVER" << '\n';
	return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int dx[4] = {0,1,0,-1};
const int dy[4] = {1,0,-1,0};
int main() {
	int a[4][4];
	REP(i, 4) REP(j, 4) cin >> a[i][j];
	bool ok = false;
	REP(i, 4) REP(j, 4) REP(k, 4)
		if (i+dx[k]>=0 && i+dx[k]<4)
			if (j+dy[k]>=0 && j+dy[k]<4)
				if (a[i][j] == a[i+dx[k]][j+dy[k]])
					ok = true;
	cout << (ok ? "CONTINUE" : "GAMEOVER") << '\n';
	return 0;
}
```