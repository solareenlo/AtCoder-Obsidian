# B - Shift and Reverse
[[順列]] [[if]] [[Brown]] [[ARC]] [[Go]]
#順列 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc132/tasks/arc132_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, p1, p2 int
	fmt.Scan(&n, &p1, &p2)

	if (p1+1)%n == p2%n {
		fmt.Println(min((n+1-p1)%n, (p1+1)%n))
	} else {
		fmt.Println(min((n-p1)%n+1, p1%n+1))
	}
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```