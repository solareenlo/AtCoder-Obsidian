# E - マスゲーム
[[BFS]] [[DFS]] [[Black]] [[Others]]
#BFS #DFS #Black #Others 

## 問題
- https://atcoder.jp/contests/code-thanks-festival-2014-b-open/tasks/code_thanks_festival_14_qualb_e

## 解き方
### Code DFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int r, c, g[50][50], visited[50][50];
int dx[4] = {1,0,-1,0};
int dy[4] = {0,1,0,-1};

void dfs(int x, int y) {
	if (x<1 || y<1 || x>c+1 || y>r+1 || g[y][x] == 0 || visited[y][x])
		return ;
	visited[y][x] = 1;
	REP(i, 4) dfs(x+dx[i], y+dy[i]);
}

int main() {
	int rs, cs, rg, cg, n; cin >> r>> c >> rs >> cs >> rg >> cg >> n;
	REP(i, n) {
		int r, c, h, w; cin >> r >> c >> h >> w;
		for (int j=r; j<r+h; j++)
			for (int k=c; k<c+w; k++)
				g[j][k] = 1;
	}
	dfs(rs, cs);
	cout << ((visited[rg][cg]) ? "YES" : "NO") << '\n';
	return 0;
}
```

### Code BFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

const int dx[4] = {1, 0, -1, 0};
const int dy[4] = {0, -1, 0, 1};

int main() {
	int h, w, sy, sx, gy, gx; cin >> h >> w >> sy >> sx >> gy >> gx;
	int n; cin >> n;
	int g[50][50] = {};
	while (n--) {
		int r, c, h, w; cin >> r >> c >> h >> w;
		for (int i=r; i<r+h; i++)
			for (int j=c; j<c+w; j++)
				g[i][j] = 1;
	}
	if (g[sy][sx] == 0 || g[gy][gx] == 0) {
		cout << "NO" << '\n';
		return 0;
	}
	bool vis[50][50] = {};
	vis[sy][sx] = true;
	queue<pair<int, int> > q;
	q.emplace(sy, sx);
	while (!q.empty()) {
		auto [y, x] = q.front(); q.pop();
		REP(i, 4) {
			int nx = x + dx[i];
			int ny = y + dy[i];
			if (0<nx && nx<=w && 0<ny && ny<=h && g[ny][nx] && !vis[ny][nx]) {
				vis[ny][nx] = true;
				q.emplace(ny, nx);
			}
		}
	}
	cout << (vis[gy][gx] ? "YES" : "NO") << '\n';
	return 0;
}
```