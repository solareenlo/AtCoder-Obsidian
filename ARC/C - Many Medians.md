# C - Many Medians
[[sort]] [[Brown]] [[ARC]] [[Go]]
#sort #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc095/tasks/arc095_a

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
	x, y := make([]int, n), make([]int, n)
	for i := range x {
		fmt.Fscan(in, &x[i])
		y[i] = x[i]
	}
	sort.Ints(y)

	index := map[int]int{}
	for i := 0; i < n; i++ {
		index[y[i]] = i + 1
	}

	for i := 0; i < n; i++ {
		if index[x[i]] <= n/2 {
			fmt.Fprintln(out, y[n/2])
		}
		if index[x[i]] >= n/2+1 {
			fmt.Fprintln(out, y[n/2-1])
		}
	}
}
```
