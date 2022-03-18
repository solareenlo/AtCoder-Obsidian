# C - Pushing Balls
[[期待値]] [[Red]] [[AGC]] [[Go]]
#期待値 #Red #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc007/tasks/agc007_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, d, x float64
	fmt.Scan(&n, &d, &x)

	a := 0.0
	for d += (n - 0.5) * x; n > 0; n-- {
		a += d
		d += d / n
	}
	fmt.Println(a)
}
```