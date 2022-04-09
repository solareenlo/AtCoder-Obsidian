# D - Swap Hats
[[転倒数]] [[Gray]] [[ABC]] [[Go]]
#転倒数 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc244/tasks/abc244_d

## 解き方
### Code
```go
package main

import "fmt"

func sign(S string) bool { return S == "RGB" || S == "GBR" || S == "BRG" }

func main() {
	s := make([]string, 3)
	t := make([]string, 3)
	fmt.Scan(&s[0], &s[1], &s[2])
	fmt.Scan(&t[0], &t[1], &t[2])

	if sign(s[0]+s[1]+s[2]) == sign(t[0]+t[1]+t[2]) {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}
}
```