# B - Office Ninja
[[BFS]] [[Hexagon]] [[ダイクストラ法]] [[Black]] [[Others]]
#BFS #Hexagon #ダイクストラ法 #Black #Others 

## 問題
- https://atcoder.jp/contests/indeednow-finala-open/tasks/indeednow_2015_finala_b

## 解き方
- 六角形の BFS．

### Code BFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for(int i=0; i<n; i++)
using namespace std;

int C, R, sx, sy, tx, ty;
int a[110][110], d[110][110];
int dx[6] = {-1,-1,0,0,1,1};
int dy[2][6] = {{-1,0,-1,1,-1,0}, {0,1,-1,1,0,1}};
char c[110][110];

signed main() {
	cin >> C >> R;
	REP(i, C) REP(j, R) {
		cin >> c[i][j];
		d[i][j] = 1e9;
		if (c[i][j] == 's') sx = i, sy = j;
		else if (c[i][j] == 't') tx = i, ty = j;
		else a[i][j] = c[i][j] - '0';
	}
	queue<pair<int, int> > q;
	q.push({sx, sy});
	d[sx][sy] = 0;
	while (!q.empty()) {
		auto [x, y] = q.front(); q.pop();
		REP(i, 6) {
			int nx = x + dx[i], ny = y + dy[x % 2][i];
			if (0 <= nx && nx < C && 0 <= ny && ny < R && d[nx][ny]>d[x][y] + a[nx][ny]) {
				q.push({nx, ny});
				d[nx][ny] = d[x][y] + a[nx][ny];
			}
		}
	}
	cout << d[tx][ty] << '\n';
	return 0;
}
```