# D - An Ordinary Game
[[xor]] [[Blue]] [[ARC]] [[Go]]
#xor #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc064/tasks/arc064_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)
	n := len(s)
	tmp := 0
	if s[0] == s[n-1] {
		tmp = 1
	}
	if (n&1)^tmp != 0 {
		fmt.Println("First")
	} else {
		fmt.Println("Second")
	}
}
```