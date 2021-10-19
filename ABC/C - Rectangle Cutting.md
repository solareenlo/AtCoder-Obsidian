# C - Rectangle Cutting
[[面積]] [[Brown]] [[ABC]] [[Go]]
#面積 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc130/tasks/abc130_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var w, h, x, y float64
	fmt.Scan(&w, &h, &x, &y)

	res := w * h / 2.0
	if x == w/2 && y == h/2 {
		fmt.Println(res, 1)
	} else {
		fmt.Println(res, 0)
	}
}
```