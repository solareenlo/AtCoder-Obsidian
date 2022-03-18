# A - STring
[[文字列]] [[Green]] [[AGC]] [[Go]]
#文字列 #Green #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc005/tasks/agc005_a

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

	var x string
	fmt.Fscan(in, &x)

	s, t := 0, 0
	for i := range x {
		if x[i] == 'S' {
			s++
		} else {
			if s != 0 {
				s--
			} else {
				t++
			}
		}
	}
	fmt.Println(s + t)
}
```