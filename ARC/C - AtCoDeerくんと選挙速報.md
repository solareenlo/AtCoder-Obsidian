# C - AtCoDeerくんと選挙速報
[[min-max]] [[Light Blue]] [[ARC]] [[Go]]
#min-max #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/abc059/tasks/arc072_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)
	for i := 0; i < n-1; i++ {
		var c, d int
		fmt.Scan(&c, &d)
		x := max((a-1)/c+1, (b-1)/d+1)
		a, b = c*x, d*x
	}
	fmt.Println(a + b)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```