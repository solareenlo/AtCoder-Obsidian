# A - Atcoder Handles
[[文字列操作]] [[辞書順]] [[Black]] [[Others]] [[Go]]
#文字列操作 #辞書順 #Black #Others #Go

## 問題
- https://atcoder.jp/contests/s8pc-4/tasks/s8pc_4_a

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
	fmt.Scan(&n)

	s := make([]string, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&s[i])
	}

	var t string
	fmt.Scan(&t)

	l, r := 1, n+1
	for i := 0; i < n; i++ {
		a := strings.Replace(s[i], "?", "a", -1)
		z := strings.Replace(s[i], "?", "z", -1)
		if a > t {
			r--
		}
		if z < t {
			l++
		}
	}

	for i := l; i <= r; i++ {
		fmt.Print(i)
		if i == r {
			fmt.Println()
		} else {
			fmt.Print(" ")
		}
	}
}
```