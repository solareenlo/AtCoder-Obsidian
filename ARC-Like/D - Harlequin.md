# D - Harlequin
[[偶奇]] [[Green]] [[ARC-Like]] [[Go]]
#偶奇 #Green #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/caddi2018/tasks/caddi2018_b

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

	v := 0
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		v |= a & 1
	}

	if v != 0 {
		fmt.Println("first")
	} else {
		fmt.Println("second")
	}
}
```