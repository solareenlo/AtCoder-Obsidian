# A - Irreversible operation
[[文字列]] [[総和]] [[Brown]] [[AGC]] [[Go]]
#文字列 #総和 #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc029/tasks/agc029_a

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

	a, b := 0, 0
	for i := range s {
		if s[i]%2 != 0 {
			a += b
		} else {
			b++
		}
	}
	fmt.Println(a)
}
```