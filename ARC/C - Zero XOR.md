# C - Zero XOR
[[xor]] [[偶奇]] [[Green]] [[ARC]] [[Go]]
#xor #偶奇 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc131/tasks/arc131_c

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

	var n int
	fmt.Fscan(in, &n)

	a := make([]int, n+1)
	v := 0
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
		v ^= a[i]
	}

	p := 0
	for i := 1; i <= n; i++ {
		if a[i] == v {
			p |= 1
		} else {
			p |= 0
		}
	}

	if p != 0 || (n&1) != 0 {
		fmt.Println("Win")
	} else {
		fmt.Println("Lose")
	}
}
```