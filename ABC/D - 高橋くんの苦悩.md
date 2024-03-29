# D - 高橋くんの苦悩
[[DP]] [[Light Blue]] [[ABC]] [[Go]]
#DP #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc015/tasks/abc015_4

## 解き方
### Code 2
```go
package main

import "fmt"

func main() {
	var w, n, k, a, b int
	fmt.Scan(&w, &n, &k)

	var dp [10001][51]int = [10001][51]int{}
	for c := 0; c < n; c++ {
		fmt.Scan(&a, &b)
		for i := w; i > a-1; i-- {
			for j := k; j > 0; j-- {
				if dp[i][j] < dp[i-a][j-1]+b {
					dp[i][j] = dp[i-a][j-1] + b
				}
			}
		}
	}
	fmt.Println(dp[w][k])
}
```

### Code 1
```go
package main

import "fmt"

func main() {
	var W, n, K, a, b int
	fmt.Scan(&W, &n, &K)

	res := 0
	var dp [51][51][10001]int = [51][51][10001]int{}
	for i := 0; i < n; i++ {
		fmt.Scan(&a, &b)
		for k := 0; k <= K; k++ {
			for w := 0; w <= W; w++ {
				dp[i+1][k][w] = max(dp[i+1][k][w], dp[i][k][w])
				if w+a <= W && k+1 <= K {
					dp[i+1][k+1][w+a] = max(dp[i+1][k+1][w+a], dp[i][k][w]+b)
				}
				res = max(res, dp[n][k][w])
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