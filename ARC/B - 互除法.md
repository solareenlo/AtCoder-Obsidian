# B - 互除法
[[ユークリッドの互助法]] [[フィボナッチ数列]] [[Green]] [[ARC]] [[Go]]
#ユークリッドの互助法 #フィボナッチ数列 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc051/tasks/arc051_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	x := 0
	y := 1
	for i := 0; i < n; i++ {
		z := x + y
		x = y
		y = z
	}

	fmt.Println(x, y)
}
```