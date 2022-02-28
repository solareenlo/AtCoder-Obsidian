# D - Bracket Score 2
[[数列]] [[括弧]] [[sort]] [[Blue]] [[ARC]] [[Go]]
#数列 #括弧 #sort #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc120/tasks/arc120_d

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	fmt.Fscan(in, &n)
	n *= 2

	type pair struct{ x, y int }
	a := make([]pair, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i].x)
		a[i].y = i
	}
	sort.Slice(a, func(i, j int) bool {
		return a[i].x < a[j].x
	})

	f := make([]int, 1000005)
	for i := 1; i <= n/2; i++ {
		f[a[i].y] = 1
	}
	c := 0
	sz := 0
	for i := 1; i <= n; i++ {
		if sz == 0 || c == f[i] {
			c = f[i]
			sz++
			fmt.Fprint(out, "(")
		} else {
			sz--
			fmt.Fprint(out, ")")
		}
	}
	fmt.Fprintln(out)
}
```