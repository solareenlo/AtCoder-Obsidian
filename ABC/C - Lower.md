# C - Lower
[[区間]] [[Gray]] [[ABC]] [[Go]]
#区間 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc139/tasks/abc139_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	h := make([]int, n)
	for i := range h {
		fmt.Scan(&h[i])
	}

	cnt, maxi := 0, 0
	for i := 0; i < n-1; i++ {
		if h[i] >= h[i+1] {
			cnt++
		} else {
			cnt = 0
		}
		maxi = max(maxi, cnt)
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