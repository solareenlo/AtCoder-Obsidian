# F - String Cards
[[文字列]] [[DP]] [[Orange]] [[ABC]] [[Go]]
#文字列 #DP #Orange #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc225/tasks/abc225_f

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	s := make([]string, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&s[i])
	}
	sort.Slice(s, func(i, j int) bool {
		return s[i]+s[j] > s[j]+s[i]
	})

	dp := make([]string, k+2)
	for i := 1; i < k+1; i++ {
		dp[i] = "~"
	}

	for i := 0; i < n; i++ {
		for j := k; j >= 0; j-- {
			if dp[j] != "~" {
				if dp[j+1] > s[i]+dp[j] {
					dp[j+1] = s[i] + dp[j]
				}
			}
		}
	}
	fmt.Println(dp[k])
}
```