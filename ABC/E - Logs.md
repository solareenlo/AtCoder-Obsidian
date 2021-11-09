# E - Logs
[[二分探索]] [[Light Blue]] [[ABC]] [[Go]]
#二分探索 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc174/tasks/abc174_e

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

	var n, k int
	fmt.Fscan(in, &n, &k)

	a := make([]int, n)
	l, r := 0, 0
	for i := range a {
		fmt.Fscan(in, &a[i])
		r = max(r, a[i])
	}

	for r-l > 1 {
		mid := (r + l) / 2
		cnt := 0
		for i := range a {
			cnt += (a[i] - 1) / mid
		}
		if cnt <= k {
			r = mid
		} else {
			l = mid
		}
	}

	fmt.Println(r)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```