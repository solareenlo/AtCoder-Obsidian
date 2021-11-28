# C - Brute-force Attack
[[文字列操作]] [[再帰関数]] [[Gray]] [[ABC]] [[Go]]
#文字列操作 #再帰関数 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc029/tasks/abc029_c

## 解き方
### Code
```go
package main

import "fmt"

func f(rest int, s string) {
	if rest == 0 {
		fmt.Println(s)
	} else {
		for c := 'a'; c < 'd'; c++ {
			f(rest-1, s+string(c))
		}
	}
}

func main() {
	var n int
	fmt.Scan(&n)
	f(n, "")
}
```