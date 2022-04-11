# D - 2-variable Function
[[全探索]] [[Green]] [[ABC]] [[Go]]
#全探索 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc246/tasks/abc246_d

## 解き方
### Code
```go
package main

import "fmt"

func f(a, b int) int {
	return (a*a*a + a*a*b + a*b*b + b*b*b)
}

func main() {
	var n int
	fmt.Scan(&n)

	x := 1 << 60
	j := 1000000
	for i := 0; i <= 1000000; i++ {
		for f(i, j) >= n && j >= 0 {
			x = min(x, f(i, j))
			j--
		}
	}
	fmt.Println(x)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```