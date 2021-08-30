# D - サプリメント
[[累積和]] [[DP]] [[尺取法]] [[Light Blue]] [[ABC]] [[Go]]
#累積和 #DP #尺取法 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc017/tasks/abc017_4

## 解き方
### Code 01
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	f := make([]int, 100_002)
	for i := 0; i < n; i++ {
		fmt.Scan(&f[i+2])
		f[i+2]--
	}

	sum := make([]int, 100_002)
	dp := make([]int, 100_002)
	dp[1] = 1
	sum[1] = 1

	mod := int(1e9 + 7)
	s := 0
	c := make([]int, 100_002)
	for i := 2; i < n+2; i++ {
		if s < c[f[i]] {
			s = c[f[i]]
		}
		dp[i] = (sum[i-1] + mod - sum[s]) % mod
		sum[i] = (sum[i-1] + dp[i]) % mod
		c[f[i]] = i - 1
	}

	fmt.Println(dp[n+1])
}
```

### Code 02
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	f := make([]int, 100_001)
	for i := 0; i < n; i++ {
		fmt.Scan(&f[i])
		f[i]--
	}

	sum, l, r, mod := 0, 0, 0, int(1e9+7)
	used := make([]bool, m)
	dp := make([]int, n+1)
	dp[0] = 1
	for r < n {
		for l < n && used[f[r]] {
			used[f[l]] = false
			sum = (sum - dp[l] + mod) % mod
			l++
		}
		used[f[r]] = true
		sum = (sum + dp[r]) % mod
		r++
		dp[r] = sum
	}
	fmt.Println(dp[n])
}
```