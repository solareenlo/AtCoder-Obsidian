# B - Not Found
[[文字列]] [[Gray]] [[ABC]] [[Go]]
#文字列 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc071/tasks/abc071_b

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

	for c := 'a'; c <= 'z'; c++ {
		if !strings.Contains(s, string(c)) {
			fmt.Println(string(c))
			return
		}
	}
	fmt.Println("None")
}
```