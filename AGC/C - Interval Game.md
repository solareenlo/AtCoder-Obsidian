# C - Interval Game
[[区間]] [[sort]] [[Yellow]] [[AGC]] [[Go]]
#区間 #sort #Yellow #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc025/tasks/agc025_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	l := make([]int, n+1)
	r := make([]int, n+1)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &l[i], &r[i])
	}
	sort.Ints(l)
	sort.Ints(r)

	ans := 0
	for i := 0; i < n; i++ {
		tmp := l[n-i] - r[i]
		if tmp < 1 {
			break
		}
		ans += tmp
	}

	fmt.Println(ans << 1)
}
```