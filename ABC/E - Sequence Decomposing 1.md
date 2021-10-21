# E - Sequence Decomposing
[[数列]] [[lower_bound]] [[upper_bound]] [[Light Blue]] [[ABC]] [[Go]]
#数列 #lower_bound #upper_bound #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc134/tasks/abc134_e

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
		dp[i] = 10
	}

	for i := 0; i < n; i++ {
		var a int
		fmt.Scan(&a)
		index := sort.SearchInts(dp, -a+1)
		dp[index] = -a
	}

	fmt.Println(sort.SearchInts(dp, 1))
}
```