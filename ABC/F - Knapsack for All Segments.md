# F - Knapsack for All Segments
[[DP]] [[Knapsack]] [[Blue]] [[ABC]] [[Go]]
#DP #Knapsack #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc159/tasks/abc159_f

## 解き方
### Code 2
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	mod := 998244353
	dp := [3003][30003][3]int{}
	dp[0][0][0] = 1
	for i := 0; i < n; i++ {
		for j := 0; j < k+1; j++ {
			dp[i+1][j][0] += dp[i][j][0]
			dp[i+1][j][0] %= mod
			dp[i+1][j][1] += dp[i][j][0] + dp[i][j][1]
			dp[i+1][j][1] %= mod
			dp[i+1][j][2] += dp[i][j][0] + dp[i][j][1] + dp[i][j][2]
			dp[i+1][j][2] %= mod
			if j+a[i] <= k {
				dp[i+1][j+a[i]][1] += dp[i][j][0] + dp[i][j][1]
				dp[i+1][j+a[i]][1] %= mod
				dp[i+1][j+a[i]][2] += dp[i][j][0] + dp[i][j][1]
				dp[i+1][j+a[i]][2] %= mod
			}
		}
	}

	fmt.Println(dp[n][k][2])
}
```

### Code 1
```go
package main

import "fmt"

func main() {
	var n, s int
	fmt.Scan(&n, &s)

	mod := 998244353
	dp := [3003]int{}
	res := 0
	for i := 0; i < n; i++ {
		var v int
		fmt.Scan(&v)
		dp[0]++
		for j := s - v; j >= 0; j-- {
			dp[j+v] = (dp[j+v] + dp[j]) % mod
		}
		res = (res + dp[s]) % mod
	}

	fmt.Println(res)
}
```