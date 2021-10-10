# C - To Infinity
[[文字列]] [[Brown]] [[ABC]] [[Go]]
#文字列 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc106/tasks/abc106_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	var k int
	fmt.Scan(&s, &k)

	for i := 0; i < min(len(s), k); i++ {
		if s[i] > '1' {
			fmt.Println(string(s[i]))
			return
		}
	}
	fmt.Println(1)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```