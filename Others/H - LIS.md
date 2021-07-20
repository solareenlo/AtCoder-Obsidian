# H - LIS
[[upper_bound]] [[sort]] [[search]] [[Black]] [[Others]] [[Go]]
#upper_bound #sort #search #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/chokudai_S001/tasks/chokudai_S001_h

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)
	dp := make([]int, n)
	for i := range dp {
		dp[i] = 1000000007
	}
	for i := 0; i < n; i++ {
		var a int
		fmt.Scan(&a)
		dp[sort.SearchInts(dp, a)] = a
	}
	fmt.Println(sort.SearchInts(dp, 1000000007))
}
```