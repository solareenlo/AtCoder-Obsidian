# D - Simple Knapsack
[[ナップサック]] [[DP]] [[Light Blue]] [[ABC]] [[Go]]
#ナップサック #DP #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc060/tasks/arc073_b

## 解き方
### Code DP02
```go
package main

import "fmt"

func main() {
	var n, W int
	fmt.Scan(&n, &W)
	w, v := [101]int{}, [101]int{}
	for i := 1; i <= n; i++ {
		fmt.Scan(&w[i], &v[i])
	}

	dp := [101][310][101]int{}
	res := 0
	for i := 1; i <= n; i++ {
		for k := 1; k <= i; k++ {
			for j := 0; j <= i*3; j++ {
				if j < w[i]-w[1] {
					dp[i][j][k] = dp[i-1][j][k]
				} else {
					dp[i][j][k] = max(dp[i-1][j][k], dp[i-1][j-w[i]+w[1]][k-1]+v[i])
				}
				if j+k*w[1] <= W {
					res = max(res, dp[n][j][k])
				}
			}
		}
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code DP01
```go
package main

import "fmt"

func main() {
	var n, W int
	fmt.Scan(&n, &W)
	w, v := [101]int{}, [101]int{}
	for i := 0; i < n; i++ {
		fmt.Scan(&w[i], &v[i])
	}
	cp := w[0]
	for i := range w {
		w[i] -= cp
	}

	res := 0
	dp := [110][350][110]int{}
	for i := 0; i < n; i++ {
		for k := 0; k <= n; k++ {
			for j := 0; j <= 310; j++ {
				dp[i+1][j+w[i]][k+1] = max(dp[i+1][j+w[i]][k+1], dp[i][j][k]+v[i])
				dp[i+1][j][k] = max(dp[i+1][j][k], dp[i][j][k])
				if j+k*cp <= W {
					res = max(res, dp[n][j][k])
				}
			}
		}
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```