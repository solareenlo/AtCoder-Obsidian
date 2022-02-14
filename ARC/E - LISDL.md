# E - LISDL
[[数列]] [[狭義単調増加]] [[Blue]] [[ARC]] [[Go]]
#数列 #狭義単調増加 #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc091/tasks/arc091_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)

	if a+b > n+1 || a*b < n {
		fmt.Println(-1)
		return
	}

	for n > 0 {
		for i := n - min(a, n-b+1) + 1; i <= n; i++ {
			fmt.Print(i, " ")
		}
		n -= min(a, n-b+1)
		b--
	}
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```