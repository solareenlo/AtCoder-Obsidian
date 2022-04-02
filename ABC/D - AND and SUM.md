# D - AND and SUM
[[2進数]] [[Green]] [[ABC]] [[Go]]
#2進数 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc238/tasks/abc238_d

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
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var t int
	fmt.Fscan(in, &t)

	for i := 0; i < t; i++ {
		var a, s int
		fmt.Fscan(in, &a, &s)
		xo := s - 2*a
		if xo >= 0 && (xo&a) == 0 {
			fmt.Fprintln(out, "Yes")
		} else {
			fmt.Fprintln(out, "No")
		}
	}
}
```