# D - Hanjo
[[全探索]] [[DFS]] [[popcount]] [[Light Blue]] [[ABC]]
#全探索 #DFS #popcount #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc196/tasks/abc196_d

## 解き方
### Code DFS
```c++
#include <bits/stdc++.h>
using namespace std;

int H, W, RES;
bool MAP[16][16];

void dfs(int y, int x, int a, int b) {
	if (x==W) y++, x=0;
	if (y==H) return (void)RES++;
	if (MAP[y][x]) return dfs(y, x+1, a, b);
	MAP[y][x] = true;
	if (b) dfs(y, x+1, a, b-1);
	if (a && !MAP[y][x+1]) {
		MAP[y][x+1] = true;
		dfs(y, x+1, a-1, b);
		MAP[y][x+1] = false;
	}
	if (a && !MAP[y+1][x]) {
		MAP[y+1][x] = true;
		dfs(y, x+1, a-1, b);
		MAP[y+1][x] = false;
	}
	MAP[y][x] = false;
}

int main() {
	int a, b; cin >> H >> W >> a >> b;
	dfs(0, 0, a, b);
	cout << RES << '\n';
	return 0;
}
```

### Code popcount
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int h, w, a; cin >> h >> w >> a;
	int dp[h+1][1<<(h*w)][a+1];
	bzero(dp, sizeof(dp));
	dp[0][0][a] = 1;
	REP(i, h) REP(j, w+1) REP(k, 1<<w) {
		int t=(1<<w)-k-1;
		if (j==w) {
			int b=__builtin_popcount(t);
			for (int l=b; l<=a; l++)
				dp[i+1][t][l-b] += dp[i][k][l];
		}
		if (t>>j&1) REP(b, a+1) {
			dp[i][k|1<<j][b]+=dp[i][k][b];
			if (b && t>>(j+1)&1)
				dp[i][k|3<<j][b-1] += dp[i][k][b];
		}
	}
	cout << dp[h][0][0] << '\n';
	return 0;
}
```