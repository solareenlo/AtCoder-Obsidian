# C - pushpush
[[数列]] [[Gray]] [[ABC]] [[Go]]
#数列 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc066/tasks/arc077_a

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

	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
	}

	for i := n - 1; i >= 0; i -= 2 {
		fmt.Fprint(out, a[i], " ")
	}
	for i := n % 2; i < n; i += 2 {
		fmt.Fprint(out, a[i], " ")
	}
	fmt.Fprintln(out)
}
```