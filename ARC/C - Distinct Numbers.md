# C - Distinct Numbers
[[数列]] [[考察]] [[Yellow]] [[ARC]] [[Go]]
#数列 #考察 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc137/tasks/arc137_c

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

	var a int
	for i := 0; i < n-1; i++ {
		fmt.Fscan(in, &a)
	}
	var b int
	fmt.Fscan(in, &b)

	if a+1 == b && (b+n)&1 != 0 {
		fmt.Println("Bob")
	} else {
		fmt.Println("Alice")
	}
}
```