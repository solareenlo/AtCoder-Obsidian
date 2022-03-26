# B - Ice Rink Game
[[区間]] [[二分探索]] [[Light Blue]] [[AGC]] [[Go]]
#区間 #二分探索 #Light_Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc020/tasks/agc020_b

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

	ans := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &ans[i])
	}

	l := 2
	r := 2
	for i := n; i >= 1; i-- {
		l = ((l-1)/ans[i] + 1) * ans[i]
		r = r/ans[i]*ans[i] + ans[i] - 1
	}

	if l > r {
		fmt.Println(-1)
	} else {
		fmt.Println(l, r)
	}
}
```