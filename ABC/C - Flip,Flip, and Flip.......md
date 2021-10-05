# C - Flip,Flip, and Flip......
[[if]] [[Gray]] [[ABC]] [[Go]]
#if #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc090/tasks/arc091_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	if n == 1 && m > 2 {
		fmt.Println(m - 2)
	} else if m == 1 && n > 2 {
		fmt.Println(n - 2)
	} else {
		fmt.Println((n - 2) * (m - 2))
	}
}
```