# C - 流れ
[[DFS]] [[BFS]] [[Black]] [[Others]]
#DFS #BFS #Black #Others

## 問題
- https://atcoder.jp/contests/fuka5/tasks/fuka_liquid

## 解き方
- 現在のマスの高さと，そのマスの四方の高さを見比べながら DFS か BFS を行う．

### Code2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int w, h, p, d[21][21];
int dx[4] = {1, -1, 0, 0};
int dy[4] = {0, 0, 1, -1};
bool visited[21][21];

void dfs(int x, int y) {
	if (visited[y][x]) return ;
	visited[y][x] = true;
	REP(i, 4) {
		int nx = x + dx[i];
		int ny = y + dy[i];
		if (0<=nx && nx<w && 0<=ny && ny<h && d[y][x]>d[ny][nx] && !visited[ny][nx])
			dfs(nx, ny);
	}
}

int main() {
	while (cin >> w >> h >> p, w || h || p) {
		REP(i, h) REP(j, w) cin >> d[i][j];
		bzero(visited, sizeof(visited));
		REP(i, p) {
			int x, y; cin >> x >> y;
			dfs(x, y);
		}
		int res = 0;
		REP(i, h) REP(j, w)
			if (visited[i][j]) res++;
		cout << res << '\n';
	}
	return 0;
}

```


### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using P = pair<int, int>;
int dx[4] = {0, 1, 0, -1};
int dy[4] = {1, 0, -1, 0};
int main() {
	int w, h, p, x, y;
	while (cin >> w >> h >> p, w || h || p) {
		int z[h][w];
		REP(i, h) REP(j, w) cin >> z[i][j];
		bool visited[h][w];
		bzero(visited, sizeof(visited));
		queue<P> q;
		REP(i, p) {
			cin >> x >> y;
			q.push({y, x});
			visited[y][x] = true;
		}
		while (!q.empty()) {
			tie(y, x) = q.front(); q.pop();
			REP(i, 4) {
				int ny = y + dy[i];
				int nx = x + dx[i];
				if (0<=ny && ny<h && 0<=nx && nx<w && z[ny][nx]<z[y][x] && !visited[ny][nx]) {
					visited[ny][nx] = true;
					q.push({ny, nx});
				}
			}
		}
		int res = 0;
		REP(i, h) REP(j, w)
			if (visited[i][j]) res++;
		cout << res << '\n';
	}
	return 0;
}
```