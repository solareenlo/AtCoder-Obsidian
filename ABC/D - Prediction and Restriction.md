# D - Prediction and Restriction
[[DP]] [[貪欲法]] [[Brown]] [[ABC]] [[Go]]
#DP #貪欲法 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc149/tasks/abc149_d

## 解き方
### Code 貪欲法
```go
package main

import "fmt"

func main() {
	var n, k, r, s, p int
	var t string
	fmt.Scan(&n, &k, &r, &s, &p, &t)

	flag := make([]bool, 100001)
	res := 0
	for i := 0; i < n; i++ {
		if i < k || t[i-k] != t[i] || !flag[i-k] {
			if t[i] == 'r' {
				res += p
			} else if t[i] == 's' {
				res += r
			} else {
				res += s
			}
			flag[i] = true
		}
	}
	fmt.Println(res)
}
```

### Code DP
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	var r, s, p int
	fmt.Scan(&r, &s, &p)

	point := make([]int, 128)
	point['r'] = p
	point['s'] = r
	point['p'] = s

	var t string
	fmt.Scan(&t)

	dp := make([][3]int, n+1)
	flag := make([]bool, 100001)

	for i := 0; i < n; i++ {
		for j := 0; j < 3; j++ {
			if i-k >= 0 && flag[i-k] && t[i] == t[i-k] {
				dp[i+1][j] = max(dp[i+1][j], dp[i][j])
			} else {
				dp[i+1][j] = max(dp[i+1][j], dp[i][j]+point[t[i]])
				flag[i] = true
			}
		}
	}

	res := 0
	for i := 0; i < 3; i++ {
		res = max(res, dp[n][i])
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