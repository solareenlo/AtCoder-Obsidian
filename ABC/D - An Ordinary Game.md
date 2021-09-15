# D - An Ordinary Game
[[xor]] [[数学的考察]] [[パターン]] [[Light Blue]] [[ABC]] [[Go]]
#xor #数学的考察 #パターン #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc048/tasks/arc064_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	res := "First"
	if (s[0] == s[n-1]) != (n%2 == 0) {
		res = "Second"
	}
	fmt.Println(res)
}
```