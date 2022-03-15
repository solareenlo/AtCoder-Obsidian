# E - Odd Sum Rectangles
[[グリッド]] [[偶奇]] [[数学的考察]] [[Orange]] [[ARC-Like]] [[Go]]
#グリッド #偶奇 #数学的考察 #Orange #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/hitachi2020/tasks/hitachi2020_e

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
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n, m int
	fmt.Scan(&n, &m)

	for i := 1; i < (1 << n); i++ {
		for j := 1; j < (1 << m); j++ {
			tmp := 0
			if (i & -i) == (j & -j) {
				tmp = 1
			}
			fmt.Fprint(out, string('0'+tmp))
		}
		fmt.Fprintln(out)
	}
}
```