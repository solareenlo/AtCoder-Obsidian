# E - Balanced Piles
[[DP]] [[Orange]] [[ARC-Like]] [[Go]]
#DP #Orange #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/diverta2019-2/tasks/diverta2019_2_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, h, d int
	fmt.Scan(&n, &h, &d)

	const mod = 1_000_000_007
	s := 0
	p := 1
	for i := 1; i <= n; i++ {
		p = p * i % mod
		s = (s + p) % mod
	}

	dp := make([]int, 1<<20)
	now := 0
	for i := 1; i <= h; i++ {
		tmp := 0
		if i <= d {
			tmp = 1
		}
		dp[i] = (now*s + p*tmp) % mod
		now = (now + dp[i]) % mod
		if i >= d {
			now = (now - dp[i-d] + mod) % mod
		}
	}
	fmt.Println(dp[h])
}
```