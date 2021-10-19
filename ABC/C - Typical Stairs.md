# C - Typical Stairs
[[DP]] [[Brown]] [[ABC]] [[Go]]
#DP #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc129/tasks/abc129_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)
	a := make([]bool, n+1)
	for i := 0; i < m; i++ {
		var tmp int
		fmt.Scan(&tmp)
		a[tmp] = true
	}

	dp := make([]int, n+1)
	dp[0] = 1

	mod := int(1e9 + 7)
	for now := 0; now < n; now++ {
		for next := now + 1; next <= min(now+2, n); next++ {
			if !a[next] {
				dp[next] += dp[now]
				dp[next] %= mod
			}
		}
	}
	fmt.Println(dp[n])
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```