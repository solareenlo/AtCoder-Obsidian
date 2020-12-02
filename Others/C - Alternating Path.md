# C - Alternating Path
[[BFS]] [[DFS]] [[Union-Find]] [[Light Blue]] [[Others]]
#BFS #DFS #Union-Find #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/aising2019/tasks/aising2019_c


## 解き方
- 各マスを頂点とし，隣り合うマスの組であって色が異なるものの間に辺を張ったグラフを考える．
- このグラフに連結成分が $k$ 個あり，このうち $i$ 番目のものは $b_i$ 個の黒マスと $w_i$ 個の白マスからなっていたとする．
- この時，答えは $\sum_{1\leq i\leq k}b_i w_i$ となる．
- あとは，$(b_1,\ w_1),\ (b_2,\ w_2),\ \cdots ,\ (b_k,\ w_k)$ の値を求めれば良いことになる．
- これはグラフ上の (BFS または DFS での) 探索，または Union-Find 木により求めることができる．

## Code
Union-Find version
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0 ; i < (n); i++)
using namespace std;
using namespace atcoder;
using ll = long long;

string s[404];
ll res, cntb, cntw;

int main() {
	int h, w; cin >> h >> w;
	dsu d(h * w);
	REP(i, h) cin >> s[i];
	REP(i, h) REP(j, w) {
		if (j < w - 1 && s[i][j] != s[i][j+1])
			d.merge(w*i+j, w*i+(j+1));
		if (i < h - 1 && s[i][j] != s[i+1][j])
			d.merge(w*i+j, w*(i+1)+j);
	}
	auto g = d.groups();
	REP(i, (int)g.size()) {
		cntb = cntw = 0;
		REP(j, (int)g[i].size()) {
			if (s[g[i][j]/w][g[i][j]%w] == '#') cntb++;
			else cntw++;
		}
		res += cntb * cntw;
	}
	cout << res << '\n';
}
```

DFS viersion
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using ll = long long;

const int dx[4] = {-1,0,1,0};
const int dy[4] = {0,1,0,-1};
string s[404];
int h, w;
bool seen[404][404];
ll cnt[2];

void dfs(int x, int y) {
	seen[x][y] = true;
	if (s[x][y] == '#') cnt[0]++;
	else cnt[1]++;
	REP(i, 4) {
		int nx = x + dx[i];
		int ny = y + dy[i];
		if (nx < 0 || h <= nx || ny < 0 || w <= ny) continue ;
		if (seen[nx][ny]) continue ;
		if (s[nx][ny] == s[x][y]) continue ;
		dfs(nx, ny);
	}
}

int main() {
	cin >> h >> w;
	REP(i, h) cin >> s[i];
	ll res = 0;
	REP(i, h) REP(j ,w) {
		cnt[0] = cnt[1] = 0;
		dfs(i, j);
		res += cnt[0] * cnt[1];
	}
	cout << res << '\n';
	return 0;
}
```