# C - Circular Addition
[[数列]] [[区間]] [[Yellow]] [[ARC]] [[Go]]
#数列 #区間 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc136/tasks/arc136_c

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

	a := make([]int, n)
	mx := 0
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
		mx = max(mx, a[i])
	}

	sum := 0
	for i := 0; i < n; i++ {
		sum += max(a[i]-a[(i+1)%n], 0)
	}
	fmt.Println(max(mx, sum))
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```