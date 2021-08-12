# G - Coinage
[[文字列操作]] [[辞書順]] [[Black]] [[Others]] [[Go]]
#文字列操作 #辞書順 #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/cf17-relay-open/tasks/relay2_g

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var l int
	fmt.Scan(&l)
	var s, t string
	fmt.Scan(&s, &t)
	if s+t > t+s {
		s, t = t, s
	}
	tmp := ""
	for l%len(s) != 0 {
		tmp += t
		l -= len(t)
	}
	for i := 0; i < (l / len(s)); i++ {
		fmt.Print(s)
	}
	fmt.Println(tmp)
}
```