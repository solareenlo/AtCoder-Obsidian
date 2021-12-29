# C - Neq Min
[[Gray]] [[ABC-Like]] [[Go]]
#Gray #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/hhkb2020/tasks/hhkb2020_c

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

	a := [200001]int{}
	mini := 0
	for i := 0; i < n; i++ {
		var p int
		fmt.Fscan(in, &p)
		a[p] = 1
		for a[mini] > 0 {
			mini++
		}
		fmt.Fprintln(out, mini)
	}
}
```