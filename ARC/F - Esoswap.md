# F - Esoswap
[[数列]] [[昇順]] [[Orange]] [[ARC]] [[Go]]
#数列 #昇順 #Orange #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc110/tasks/arc110_f

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

	var n int
	fmt.Fscan(in, &n)

	p := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &p[i])
	}
	fmt.Fprintln(out, (n+99)*1000)

	for j := 0; j < 1000; j++ {
		for i := 0; i < n; i++ {
			fmt.Fprintln(out, i)
		}
		for i := 0; i < 99; i++ {
			fmt.Fprintln(out, 0)
		}
	}
}
```