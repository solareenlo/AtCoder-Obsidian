# B - ツリーグラフ
[[Tree]] [[DFS]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#Tree #DFS #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc030/tasks/arc030_2

## 解き方
- 与えられたグラフから出発点を根とした根付き木を構成し，深さ優先探索を行う．
- その際に，自分より向こう側に宝石があると，その道を行き帰りで通ることになるので，答えに $2$ を足す．
- そして，根に宝石があった場合は，行き帰りで2回その道を通ることになるので，$2$ を返す．宝石がない場合は，$0$ を返す．

### Code Go
```go
package main

import "fmt"

var (
	seen = [101]bool{}
	G    = make([][]int, 101)
	h    = [101]int{}
)

func dfs(v int) int {
	if seen[v] {
		return 0
	}
	seen[v] = true
	res := 0
	for _, nv := range G[v] {
		res += dfs(nv)
	}
	if res == 0 {
		if h[v] != 0 {
			return 2
		} else {
			return 0
		}
	}
	return res + 2
}

func main() {
	var n, x int
	fmt.Scan(&n, &x)
	x--

	for i := 0; i < n; i++ {
		fmt.Scan(&h[i])
	}
	for i := 0; i < n-1; i++ {
		var a, b int
		fmt.Scan(&a, &b)
		a--
		b--
		G[a] = append(G[a], b)
		G[b] = append(G[b], a)
	}

	fmt.Println(max(dfs(x)-2, 0))
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

bool seen[101];
vector<int> G[101];
int h[101];

int dfs(int v) {
	if (seen[v]) return 0;
	seen[v] = true;
	int res = 0;
	for (int nv : G[v])
		res += dfs(nv);
	if (res == 0) {
		if (h[v]) return 2;
		else return 0;
	}
	return res + 2;
}

int main() {
	int n, x; cin >> n >> x;
	x--;
	REP(i, n) cin >> h[i];
	REP(i, n-1) {
		int a, b; cin >> a >> b;
		a--, b--;
		G[a].push_back(b);
		G[b].push_back(a);
	}
	cout << max(dfs(x)-2, 0) << '\n';
	return 0;
}
```