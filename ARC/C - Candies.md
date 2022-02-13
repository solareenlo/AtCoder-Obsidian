# C - Candies
[[全探索]] [[探索]] [[DP]] [[Gray]] [[ARC]] [[Go]]
#全探索 #探索 #DP #Gray #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc090/tasks/arc090_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	a := make([][]int, 2)
	for i := 0; i < 2; i++ {
		a[i] = make([]int, n)
		for j := 0; j < n; j++ {
			fmt.Scan(&a[i][j])
		}
	}

	maxi := 0
	for i := 0; i < n; i++ {
		sum := 0
		for j := 0; j < n-i; j++ {
			sum += a[0][j]
		}
		for j := 0; j < i+1; j++ {
			sum += a[1][n-1-j]
		}
		maxi = max(maxi, sum)
	}
	fmt.Println(maxi)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code DP
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	a, dp := [2][101]int{}, [2][101]int{}
	for i := 0; i < 2; i++ {
		for j := 0; j < n; j++ {
			fmt.Scan(&a[i][j])
		}
	}
	dp[0][0] = a[0][0]
	for i := 0; i < 2; i++ {
		for j := 0; j < n; j++ {
			if i != 0 {
				dp[i][j] = max(dp[i][j], dp[i-1][j]+a[i][j])
			}
			if j != 0 {
				dp[i][j] = max(dp[i][j], dp[i][j-1]+a[i][j])
			}
		}
	}
	fmt.Println(dp[1][n-1])
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```