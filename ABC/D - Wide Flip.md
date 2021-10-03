# D - Wide Flip
[[文字列]] [[min-max]] [[Light Blue]] [[ABC]] [[Go]]
#文字列 #min-max #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc083/tasks/arc088_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	res := n
	for i := 1; i < n; i++ {
		if s[i-1] != s[i] {
			res = min(res, max(i, n-i))
		}
	}
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```