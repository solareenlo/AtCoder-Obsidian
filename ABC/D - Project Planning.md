# D - Project Planning
[[二分探索]] [[Blue]] [[ABC]] [[Go]] 
#二分探索 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc227/tasks/abc227_d

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

	v := make([]int, n)
	for i := range v {
		fmt.Fscan(in, &v[i])
	}

	ok, ng := 0, int(1e18)/k
	for ng-ok > 1 {
		mid := (ok + ng) / 2
		sum := 0
		for i := range v {
			sum += min(v[i], mid)
		}
		if sum >= k*mid {
			ok = mid
		} else {
			ng = mid
		}
	}
	fmt.Println(ok)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```