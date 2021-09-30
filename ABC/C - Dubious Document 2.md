# C - Dubious Document 2
[[文字列操作]] [[文字列挿入]] [[Brown]] [[ABC]] [[Go]]
#文字列操作 #文字列挿入 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc076/tasks/abc076_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var s, t string
	fmt.Scan(&t, &s)
	for i := len(t) - len(s); i >= 0; i-- {
		r, g := t, true
		for j := range s {
			if !(t[i+j] == '?' || t[i+j] == s[j]) {
				g = false
				break
			}
			r = r[:i+j] + string(s[j]) + r[i+j+1:]
		}
		if g {
			fmt.Println(strings.Replace(r, "?", "a", -1))
			return
		}
	}
	fmt.Println("UNRESTORABLE")
}
```