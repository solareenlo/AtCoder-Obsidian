# A - 塗り絵
[[if]] [[図形]] [[Brown]] [[ARC]] [[Go]]
#if #図形 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc051/tasks/arc051_a

## 解き方
### Code
```go
package main

import "fmt"

var (
	a int
	b int
	r int
)

func s(A, B int) bool {
	return (A-a)*(A-a)+(B-b)*(B-b) > r*r
}

func main() {
	var c, d, e, f int
	fmt.Scan(&a, &b, &r, &c, &d, &e, &f)
	if a-r < c || a+r > e || b-r < d || b+r > f {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
	if s(c, d) || s(c, f) || s(e, d) || s(e, f) {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```