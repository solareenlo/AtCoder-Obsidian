# B - ss
[[文字列操作]] [[Gray]] [[ABC]] [[Go]]
#文字列操作 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc066/tasks/abc066_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)
	cnt := 0
	for {
		s = s[:len(s)-2]
		cnt++
		if len(s)%2 != 0 {
			continue
		}
		m := len(s) / 2
		if s[:m] == s[m:] {
			break
		}
	}
	fmt.Println(len(s))
}
```