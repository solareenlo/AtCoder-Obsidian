# C - Knot Puzzle
[[区間]] [[Light Blue]] [[AGC]] [[Go]]
#区間 #Light_Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc002/tasks/agc002_c

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
	a := make([]int, 100005)
	fmt.Fscan(in, &n, &m, &a[0])

	p := 0
	for i := 1; i < n; i++ {
		fmt.Fscan(in, &a[i])
		if a[i]+a[i-1] >= m {
			p = i
		}
	}

	if p == 0 {
		fmt.Fprintln(out, "Impossible")
	} else {
		fmt.Fprintln(out, "Possible")
		for i := 1; i < p; i++ {
			fmt.Fprintln(out, i)
		}
		for i := n - 1; i >= p; i-- {
			fmt.Fprintln(out, i)
		}
	}
}
```