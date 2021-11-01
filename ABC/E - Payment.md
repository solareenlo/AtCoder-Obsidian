# E - Payment
[[桁]] [[文字列]] [[Light Blue]] [[ABC]] [[Go]]
#桁 #文字列 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc155/tasks/abc155_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	a, b := 0, 1
	for i := range s {
		x := int(s[i] - '0')
		tmp := a
		a = min(a+x, b+10-x)
		b = min(tmp+x+1, b+9-x)
	}

	fmt.Println(a)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```