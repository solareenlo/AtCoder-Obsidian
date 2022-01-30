# A - みんなでワイワイみかん
[[考察]] [[Brown]] [[ARC]] [[Go]]
#考察 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc056/tasks/arc056_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, k, l int
	fmt.Scan(&a, &b, &k, &l)

	ans1 := ((k / l) + 1) * b
	ans2 := (k/l)*b + (k%l)*a
	ans3 := a * k

	ans1 = min(ans1, ans2)
	ans1 = min(ans1, ans3)
	fmt.Println(ans1)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```