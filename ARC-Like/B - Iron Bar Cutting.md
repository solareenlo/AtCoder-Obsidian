# B - Iron Bar Cutting
[[累積和]] [[Gray]] [[ARC-Like]] [[Go]]
#累積和 #Gray #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/ddcc2020-qual/tasks/ddcc2020_qual_b

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
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
		a[i] += a[i-1]
	}

	ans := 1 << 60
	for i := 1; i <= n; i++ {
		ans = min(ans, abs(a[i]-(a[n]-a[i])))
	}
	fmt.Println(ans)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```