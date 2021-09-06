# C - 数式の書き換え
[[文字列操作]] [[Brown]] [[ABC]] [[Go]]
#文字列操作 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc033/tasks/abc033_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var s string
	fmt.Scan(&s)

	t := strings.Split(s, "+")
	res := 0
	for i := range t {
		if !strings.Contains(t[i], "0") {
			res++
		}
	}
	fmt.Println(res)
}
```