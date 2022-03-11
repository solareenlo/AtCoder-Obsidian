# D - Modulo Operations
[[DP]] [[Yellow]] [[ARC-Like]] [[Go]]
#DP #Yellow #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/exawizards2019/tasks/exawizards2019_d

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

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, x int
	fmt.Fscan(in, &n, &x)

	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}
	tmp := a[1 : n+1]
	sort.Ints(tmp)

	const mod = 1_000_000_007
	dp := [202][100005]int{}
	for j := 0; j <= x; j++ {
		dp[1][j] = j % a[1]
	}

	for i := 2; i <= n; i++ {
		for j := 0; j <= x; j++ {
			dp[i][j] = (dp[i-1][j%a[i]] + dp[i-1][j]*(i-1)%mod) % mod
		}
	}

	fmt.Println(dp[n][x])
}
```