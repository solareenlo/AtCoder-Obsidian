# F - Sweet Alchemy
[[Knapsack]] [[DP]] [[DFS]] [[Red]] [[ARC]] [[Go]]
#Knapsack #DP #DFS #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc096/tasks/arc096_d

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

const N = 55

type node struct{ v, id, w int }

var (
	V  int
	dp = [N * N * N]int{}
	G  = make([][]int, N)
	a  = make([]node, N)
)

func dfs(u int) {
	for _, v := range G[u] {
		dfs(v)
		a[u].v += a[v].v
		a[u].w += a[v].w
	}
}

func ins(v, w int) {
	for i := V; i >= v; i-- {
		dp[i] = min(dp[i], dp[i-v]+w)
	}
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, m, d int
	fmt.Fscan(in, &n, &m, &d, &a[1].w)
	a[1].v = 1
	a[1].id = 1

	for i := 2; i <= n; i++ {
		var x int
		fmt.Fscan(in, &a[i].w, &x)
		a[i].v = 1
		G[x] = append(G[x], i)
	}

	dfs(1)

	for i := range dp {
		dp[i] = 1 << 60
	}
	dp[0] = 0

	V = n * n * n
	lim := min(n, d)
	for i := 1; i <= n; i++ {
		x := lim
		for j := 1; j <= x; j <<= 1 {
			ins(j*a[i].v, j*a[i].w)
			x -= j
		}
		if x != 0 {
			ins(x*a[i].v, x*a[i].w)
		}
	}

	tmp := a[1 : n+1]
	sort.Slice(tmp, func(i, j int) bool {
		return tmp[i].v*tmp[j].w > tmp[i].w*tmp[j].v
	})
	for a[n].id != 1 {
		n--
	}

	ans := 0
	for i := 0; i <= V && dp[i] <= m; i++ {
		v := i
		w := dp[i]
		for j := 1; j < n; j++ {
			k := min(d-lim, (m-w)/a[j].w)
			v += k * a[j].v
			w += k * a[j].w
		}
		k := (m - w) / a[n].w
		ans = max(ans, v+k*a[n].v)
	}
	fmt.Println(ans)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```