# C - 1111gal password
[[桁]] [[DP]] [[Brown]] [[ABC]] [[Go]]
#桁 #DP #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc242/tasks/abc242_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	dp := [1000006][11]int{}
	for i := 1; i < 10; i++ {
		dp[1][i] = 1
	}

	const mod = 998244353
	ans := 0
	for i := 2; i <= n; i++ {
		for j := 1; j < 10; j++ {
			dp[i][j] = dp[i-1][j-1] + dp[i-1][j+1] + dp[i-1][j]
			dp[i][j] %= mod
			if i == n {
				ans = ans + dp[i][j]
				ans %= mod
			}
		}
	}
	fmt.Println(ans)
}
```