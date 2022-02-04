# F - Infinite Sequence
[[DP]] [[数列]] [[Yellow]] [[ARC]] [[Go]]
#DP #数列 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc071/tasks/arc071_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	mod := 1_000_000_007
	dp := make([]int, n+2)
	dp[n] = n
	dp[n-1] = n * n % mod
	s := 0
	for i := n - 2; i > 0; i-- {
		s += dp[i+3]
		s %= mod
		dp[i] = (dp[i+1] + (n-1)*(n-1) + s + i + 1) % mod
	}

	fmt.Println(dp[1])
}
```