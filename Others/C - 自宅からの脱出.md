# C - 自宅からの脱出
[[BFS]] [[Black]] [[Others]]
#BFS #Black #Others 

## 問題
- https://atcoder.jp/contests/wupc2012/tasks/wupc2012_3

## 解き方
- スタートから PC までと，PC からゴールまでの BFS を2回行う．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using P = pair<int, int>;

const int dx[4] = {0, 1, 0, -1};
const int dy[4] = {1, 0, -1, 0};
int n, m;

inline int bfs(int sy, int sx, int gy, int gx, string s[])
{
	queue<P> q;
	q.push({sy, sx});
	vector<vector<int> > dist(n, vector<int>(m, -1));
	dist[sy][sx] = 0;
	while (!q.empty()) {
		int x, y;
		tie(y, x) = q.front(); q.pop();
		REP(i, 4) {
			int nx = x + dx[i];
			int ny = y + dy[i];
			if (s[ny][nx] == '#') continue ;
			if (nx < 0 || m <= nx || ny < 0 || n <= ny) continue ;
			if (dist[ny][nx] != -1) continue ;
			dist[ny][nx] = dist[y][x] + 1;
			q.push({ny, nx});
		}
	}
	return dist[gy][gx];
}

int main() {
	cin >> n >> m;
	string s[n];
	REP(i, n) cin >> s[i];
	int sx, sy, cx, cy, gx, gy;
	REP(i, n) REP(j, m) {
		if (s[i][j] == 'S') sy = i, sx = j;
		if (s[i][j] == 'C') cy = i, cx = j;
		if (s[i][j] == 'G') gy = i, gx = j;
	}
	int res1 = bfs(sy, sx, cy, cx, s);
	int res2 = bfs(cy, cx, gy, gx, s);
	if (res1 == -1 || res2 == -1) cout << -1 << '\n';
	else cout << res1 + res2 << '\n';
	return 0;
}
```