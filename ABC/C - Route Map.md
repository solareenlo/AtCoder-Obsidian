# C - Route Map
[[文字列]] [[Gray]] [[ABC]] [[Go]]
#文字列 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc236/tasks/abc236_c

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

	var n, m int
	fmt.Fscan(in, &n, &m)

	s := make([]string, n)
	for i := range s {
		fmt.Fscan(in, &s[i])
	}

	x := 0
	for i := 0; i < m; i++ {
		var t string
		fmt.Fscan(in, &t)
		for ; t != s[x]; x++ {
			fmt.Fprintln(out, "No")
		}
		fmt.Fprintln(out, "Yes")
		x++
	}
}
```