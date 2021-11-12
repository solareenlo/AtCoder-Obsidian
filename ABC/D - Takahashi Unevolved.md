# D - Takahashi Unevolved
[[log]] [[Brown]] [[ABC]] [[Go]]
#log #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc180/tasks/abc180_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x, y, a, b int
	fmt.Scan(&x, &y, &a, &b)

	res := 0
	for y/x > a && x*a <= x+b {
		x *= a
		res++
	}

	res += (y - 1 - x) / b
	fmt.Println(res)
}
```