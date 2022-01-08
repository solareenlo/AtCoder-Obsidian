# C - 魂の還る場所
[[文字列]] [[count]] [[Light Blue]] [[ARC]] [[Go]]
#文字列 #count #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc014/tasks/arc014_3

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var n int
	var s string
	fmt.Scan(&n, &s)

	res := 0
	res += strings.Count(s, "R") % 2
	res += strings.Count(s, "G") % 2
	res += strings.Count(s, "B") % 2

	fmt.Println(res)
}
```