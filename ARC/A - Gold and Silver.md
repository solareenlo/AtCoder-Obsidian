# A - Gold and Silver
[[swap]] [[Brown]] [[ARC]] [[Go]]
#swap #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc128/tasks/arc128_a

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

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}

	b := make([]int, n)
	for i := 0; i < n-1; i++ {
		if a[i] > a[i+1] {
			b[i] ^= 1
			b[i+1] ^= 1
		}
	}

	for i := 0; i < n; i++ {
		fmt.Fprint(out, b[i], " ")
	}
}
```