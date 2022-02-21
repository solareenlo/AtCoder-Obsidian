# C - Solutions
[[区間スケジューリング]] [[貪欲法]] [[Light Blue]] [[ARC]] [[Go]]
#区間スケジューリング #貪欲法 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc106/tasks/arc106_c

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

	if m < 0 || m > max(0, n-2) {
		fmt.Fprintln(out, -1)
	} else {
		fmt.Fprintln(out, 1, 3+4*m)
		for i := 0; i < n-1; i++ {
			fmt.Fprintln(out, 2+i*4, (i+1)*4)
		}
	}
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```