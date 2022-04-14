# B - 01 Generation
[[数列]] [[flip]] [[Green]] [[ARC]] [[Go]]
#数列 #flip #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc138/tasks/arc138_b

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
	r := n
	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}

	l := 1
	flip := 0
	for l <= r {
		if a[r]^flip == 0 {
			r--
		} else if a[l]^flip == 0 {
			l++
			flip ^= 1
		} else {
			fmt.Println("No")
			return
		}
	}
	fmt.Println("Yes")
}
```