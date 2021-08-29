# D - 阿弥陀
[[DP]] [[ダブリング]] [[Blue]] [[ABC]] [[Go]]
#DP  #ダブリング #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc013/tasks/abc013_4

## 解き方
### Code DP
```go
package main

import "fmt"

func main() {
	var n, m, d, a int
	fmt.Scan(&n, &m, &d)

	dp := [30][100001]int{}
	for i := 0; i < n; i++ {
		dp[0][i] = i
	}
	for i := 0; i < m; i++ {
		fmt.Scan(&a)
		dp[0][a-1], dp[0][a] = dp[0][a], dp[0][a-1]
	}

	for i := 1; i < 30; i++ {
		for j := 0; j < n; j++ {
			dp[i][j] = dp[i-1][dp[i-1][j]]
		}
	}

	res := [100001]int{}
	for i := 0; i < n; i++ {
		now := i
		for j := 0; j < 30; j++ {
			if d>>j&1 == 1 {
				now = dp[j][now]
			}
		}
		res[now] = i
	}
	for i := 0; i < n; i++ {
		fmt.Println(res[i] + 1)
	}
}
```

### Code
```go
package main

import "fmt"

func main() {
	var n, m, d, t int
	fmt.Scan(&n, &m, &d)

	a := make([]int, n)
	c := make([]int, n)
	for i := range a {
		a[i] = i
		c[i] = i
	}
	for i := 0; i < m; i++ {
		fmt.Scan(&t)
		a[t-1], a[t] = a[t], a[t-1]
	}

	b := make([]int, n)
	for ; d > 0; d /= 2 {
		if d%2 != 0 {
			for i := 0; i < n; i++ {
				c[i] = a[c[i]]
			}
		}
		for i := 0; i < n; i++ {
			b[i] = a[i]
		}
		for i := 0; i < n; i++ {
			a[i] = b[a[i]]
		}
	}

	res := make([]int, n)
	for i := range res {
		res[c[i]] = i
	}
	for i := range res {
		fmt.Println(res[i] + 1)
	}
}
```