# D - アンバランス
[[パターン]] [[文字列]] [[Green]] [[ABC]] [[Go]]
#パターン #文字列 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc043/tasks/arc059_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	l, r := -1, -1
	for i := 1; i < len(s); i++ {
		if s[i-1] == s[i] {
			l, r = i, i+1
		}
	}
	for i := 2; i < len(s); i++ {
		if s[i-2] == s[i] {
			l, r = i-1, i+1
		}
	}
	fmt.Println(l, r)
}
```