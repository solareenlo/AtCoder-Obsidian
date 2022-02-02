# C - 一次元リバーシ
[[文字列]] [[Brown]] [[ARC]] [[Go]]
#文字列 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc063/tasks/arc063_a

## 解き方
### Code
```go
package main

import (
	"fmt"
)

func main() {
	var s string
	fmt.Scan(&s)

	cnt := 0
	for i := 1; i < len(s); i++ {
		if s[i] != s[i-1] {
			cnt++
		}
	}
	fmt.Println(cnt)
}
```