# D - 停止問題
[[DFS]] [[Brown]] [[Others]]
#DFS #Brown #Others 

## 問題
- https://atcoder.jp/contests/utpc2011/tasks/utpc2011_4

## 解き方
- 条件に則して，DFS．

```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int v[21][21][21][21], r, c;
char m[24][24];
const int dx[5] = {0, 0, 0, -1, 1};
const int dy[5] = {0, -1, 1, 0, 0};

void dfs(int x, int y, int sum, int turn) {
	if (x == r) x = 0;
	if (y == c) y = 0;
	if (x == -1) x = r - 1;
	if (y == -1) y = c - 1;
	if (v[x][y][sum][turn]) return ;
	v[x][y][sum][turn] = 1;
	char ch = m[x][y];
	if (ch == '<') turn = 1;
	else if (ch == '>') turn = 2;
	else if (ch == '^') turn = 3;
	else if (ch == 'v') turn = 4;
	else if (ch == '_') turn = (sum) ? 1 : 2;
	else if (ch == '|') turn = (sum) ? 3 : 4;
	else if (ch == '?') {
		for (int i = 1; i <= 4; i++)
			dfs(x+dx[i], y+dy[i], sum, i);
	}
	else if (ch == '.') {
		// do nothing
	}
	else if (ch == '@') {
		cout << "YES" << '\n';
		exit(0);
	}
	else if ('0' <= ch && ch <= '9') sum = ch - '0';
	else if (ch == '+') sum = (sum == 15) ? 0 : sum + 1;
	else if (ch == '-') sum = (sum == 0) ? 15 : sum - 1;
	dfs(x+dx[turn], y+dy[turn], sum, turn);
}

int main() {
	cin >> r >> c;
	REP(i, r) REP(j, c) cin >> m[i][j];
	dfs(0, 0, 0, 2);
	cout << "NO" << '\n';
	return 0;
}
```