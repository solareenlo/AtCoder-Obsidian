# A - Arithmetic Sequence
[[等差数列]] [[次元削除]] [[Gray]] [[ARC]]
#等差数列 #次元削除 #Gray #ARC 

## 問題
- https://atcoder.jp/contests/arc123/tasks/arc123_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, c int
	fmt.Scan(&a, &b, &c)
	x := 2*b - a - c
	var k int
	if x >= 0 {
		k = 0
	} else {
		k = (1 - x) / 2
	}
	fmt.Println(x + 3*k)
}
```