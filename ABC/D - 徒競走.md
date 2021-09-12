# D - 徒競走
[[bitDP]] [[DP]] [[Light Blue]] [[ABC]] [[Go]]
#bitDP #DP #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc041/tasks/abc041_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	g := make([]int, n)
	var x, y int
	for i := 0; i < m; i++ {
		fmt.Scan(&x, &y)
		x--
		y--
		g[x] |= 1 << y
	}

	dp := make([]int, 1<<n)
	dp[0] = 1
	for bit := 0; bit < 1<<n; bit++ {
		for i := 0; i < n; i++ {
			if (bit&(1<<i) != 0) && (bit|g[i] == bit) {
				dp[bit] += dp[bit-(1<<i)]
			}
		}
	}

	fmt.Println(dp[1<<n-1])
}
```