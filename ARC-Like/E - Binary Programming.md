# E - Binary Programming
[[文字列]] [[2進数]] [[Red]] [[ARC-Like]] [[Go]]
#文字列 #2進数 #Red #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/nomura2020/tasks/nomura2020_e

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

	var c string
	fmt.Fscan(in, &c)
	n := len(c)
	c = " " + c

	ans := 0
	x, y := 0, 0
	for i := 1; i <= n; i++ {
		if c[i] == '1' {
			x++
			ans += (x + 1) >> 1
		} else {
			y++
		}
	}

	m := 0
	d := make([]int, 200002)
	for i := 1; i <= n; i++ {
		if c[i] == '1' {
			if d[m] == '1' {
				m--
			} else {
				m++
				d[m] = '1'
			}
		} else {
			m++
			d[m] = '0'
		}
	}

	x = 0
	for i := 1; i <= y; i++ {
		ans += (n - m) >> 1
	}

	z := 0
	for i := 1; i <= m; i++ {
		if d[i] == '1' {
			x++
			tmp := (z + 1) >> 1
			if x&1 != 0 {
				tmp = z >> 1
			}
			ans += tmp + y - z
		} else {
			z++
		}
	}

	fmt.Println(ans)
}
```