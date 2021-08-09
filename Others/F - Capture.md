# F - Capture
[[DP]] [[範囲]] [[Black]] [[Others]] [[Go]]
#DP #範囲 #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/cf17-relay-open/tasks/relay2_f

## 解き方
### Code dp
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
	fmt.Scan(&n)

	x := make([]int, n+1)
	s := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &x[i], &s[i])
	}
	dp := make([]int, n+1)
	res := 0
	for i := 1; i <= n; i++ {
		dp[i] = max(s[i], dp[i-1]+s[i]-(x[i]-x[i-1]))
		res = max(res, dp[i])
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code 2
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	var n, x, s, f, px, res int
	fmt.Scan(&n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &x, &s)
		f = max(f+px-x+s, s)
		res = max(res, f)
		px = x
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```