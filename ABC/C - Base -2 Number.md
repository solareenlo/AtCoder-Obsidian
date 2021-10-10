# C - Base -2 Number
[[2進数]] [[文字列]] [[Green]] [[ABC]] [[Go]]
#2進数 #文字列 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc105/tasks/abc105_c

## 解き方
### Code
```go
package main

import (
	"fmt"
)

func main() {
	var n int
	fmt.Scan(&n)

	res := ""
	if n == 0 {
		res = "0"
	}
	for n != 0 {
		if n%2 == 0 {
			res = "0" + res
		} else {
			n--
			res = "1" + res
		}
		n /= -2
	}
	fmt.Println(res)
}
```