# D - Even Relation
[[Tree]] [[DFS]] [[BFS]] [[Light Blue]] [[ABC]] [[Go]] [[CPP]]
#Tree #DFS #BFS #Light_Blue #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc126/tasks/abc126_d

## 解き方
- 与えられたグラフを適当な頂点を根とみなした根付き木として考える．
- また根から頂点 $i$ への距離を $d_i$ とする．
- 任意の 2 頂点 $u$ と $v$ について，その最小共通祖先を $w$ とすると，$u$ と $v$ の距離は $d_u + d_v − 2d_w$ と書くことができる．
- この式の第 $3$ 項は偶数なので，$d_u$ と $d_w$ の偶奇が等しいときに限り，$u$ と $w$ の距離は偶数になる．
- よって例えば $d_i$ が偶数の頂点は白に，奇数の頂点は黒に塗ることで条件を満たす塗り分けが可能となる．

### Code DFS Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

type pair struct{ to, color int }

var G [][]pair = make([][]pair, 100001)
var res [100001]int

func dfs(now, pre, color int) {
	res[now] = color
	for _, g := range G[now] {
		if g.to != pre {
			dfs(g.to, now, color^(g.color&1))
		}
	}
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	var u, v, w int
	for i := 1; i < n; i++ {
		fmt.Fscan(in, &u, &v, &w)
		G[u] = append(G[u], pair{v, w})
		G[v] = append(G[v], pair{u, w})
	}
	dfs(1, 0, 0)
	for i := 1; i < n+1; i++ {
		fmt.Println(res[i])
	}
}
```

### Code DFS CPP
```c++
#include <bits/stdc++.h>
using namespace std;
using P = pair<int, int>;

vector<P> G[100001];
int RES[100001];

void dfs(int now, int pre, int color) {
	RES[now] = color;
	for (auto g : G[now])
		if (g.first != pre)
			dfs(g.first, now, color^(g.second&1));
}

int main() {
	int n; cin >> n;
	for (int i = 1; i < n; i++) {
		int u, v, w; cin >> u >> v >> w;
		G[u].emplace_back(v, w);
		G[v].emplace_back(u, w);
	}
	dfs(1, 0, 0);
	for (int i = 1; i <= n; i++)
		cout << RES[i] << '\n';
}
```

### Code BFS CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using P = pair<int, int>;

int main() {
	int n; cin >> n;
	vector<vector<P> > g(n);
	REP(i, n-1) {
		int a, b, w; cin >> a >> b >> w; a--; b--;
		g[a].push_back(make_pair(b, w));
		g[b].push_back(make_pair(a, w));
	}
	vector<int> res(n, -1);
	queue<int> q;
	res[0] = 0;
	q.push(0);
	while (!q.empty()) {
		int v = q.front();
		q.pop();
		for (auto p : g[v]) {
			int a = p.first;
			int b = p.second;
			if (res[a] != -1) continue ;
			res [a] = (res[v] + b) % 2;
			q.push(a);
		}
	}
	for (int x : res) cout << x << '\n';
    return 0;
}
```