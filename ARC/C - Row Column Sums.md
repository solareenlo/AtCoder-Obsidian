# C - Row Column Sums
[[グリッド]] [[Light Blue]] [[ARC]] [[Go]]
#グリッド #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc133/tasks/arc133_c

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

	var n, m, k int
	fmt.Fscan(in, &n, &m, &k)

	totA, c := 0, 0
	for i := 1; i <= n; i++ {
		var x int
		fmt.Fscan(in, &x)
		totA += x
		c += (m*(k-1) - x + k) % k
	}

	totB, d := 0, 0
	for i := 1; i <= m; i++ {
		var x int
		fmt.Fscan(in, &x)
		totB += x
		d += (n*(k-1) - x + k) % k
	}

	ans := n * m * (k - 1)
	if totA%k == totB%k {
		if c > d {
			fmt.Println(ans - c)
		} else {
			fmt.Println(ans - d)
		}
	} else {
		fmt.Println(-1)
	}
}
```