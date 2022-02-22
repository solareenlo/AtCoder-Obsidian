# D - Number of Multisets
[[DP]] [[Yellow]] [[ARC]] [[Go]]
#DP #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc107/tasks/arc107_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	const mod = 998244353
	dp := [3030][6060]int{}
	dp[0][0] = 1
	for i := 1; i <= n; i++ {
		for j := i; j > 0; j-- {
			dp[i][j] = (dp[i][2*j] + dp[i-1][j-1]) % mod
		}
	}
	fmt.Println(dp[n][k])
}
```