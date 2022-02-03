# F - Solitaire
[[DP]] [[考察]] [[Red]] [[ARC]] [[Go]]
#DP #考察 #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc068/tasks/arc068_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	const mod = 1_000_000_007

	var n, k int
	fmt.Scan(&n, &k)

	dp := [2002][2002]int{}
	dp[1][1] = 1
	for i := 2; i <= n; i++ {
		for j := 1; j <= min(i, k); j++ {
			dp[i][j] = (dp[i-1][j] + dp[i][j-1]) % mod
		}
	}

	ans := dp[n][k]
	for i := k + 2; i <= n; i++ {
		ans = (ans + ans) % mod
	}
	fmt.Println(ans)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```