# C - kasaka
[[文字列]] [[Gray]] [[ABC]] [[Go]]
#文字列 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc237/tasks/abc237_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var s string
	fmt.Fscan(in, &s)

	for i, j := 0, len(s)-1; i < j; {
		if s[i] == s[j] {
			j--
			i++
		} else if s[j] != 'a' {
			fmt.Println("No")
			return
		} else {
			j--
		}
	}
	fmt.Println("Yes")
}
```