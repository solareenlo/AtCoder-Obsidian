# D - Ki
[[DFS]] [[Tree]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#DFS #Tree #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc138/tasks/abc138_d

## 解き方
- 深さ優先探索 の改変
- 自分の子に自分の値を足していく．

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

var (
	g   = make([][]int, 200001)
	res [200001]int
)

func dfs(i, p int) {
	for _, x := range g[i] {
		if x != p {
			res[x] += res[i]
			dfs(x, i)
		}
	}
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, q int
	fmt.Fscan(in, &n, &q)

	for i := 0; i < n-1; i++ {
		var a, b int
		fmt.Fscan(in, &a, &b)
		a--
		b--
		g[a] = append(g[a], b)
		g[b] = append(g[b], a)
	}

	for i := 0; i < q; i++ {
		var p, x int
		fmt.Fscan(in, &p, &x)
		p--
		res[p] += x
	}

	dfs(0, 0)

	fmt.Println(strings.Trim(fmt.Sprint(res[:n]), "[]"))
}
```

## Code CPP
```C++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

vector<vector<int> > G(2e5 + 1);
vector<int> res(2e5 + 1);

void dfs(int i, int p) {
	for (int x : G[i]) {
		if (x == p) continue ;
		res[x] += res[i];
		dfs(x, i);
	}
}

int main() {
	cin.tie(0)->sync_with_stdio(false);

	int n, q; cin >> n >> q;
	REP(i, n - 1) {
		int a, b; cin >> a >> b;
		G[--a].push_back(--b);
		G[b].push_back(a);
	}
	REP(i, q) {
		int p, x; cin >> p >> x;
		res[--p] += x;
	}
	dfs(0, 0);
	REP(i, n) cout << res[i] << " ";
	return 0;
}
```