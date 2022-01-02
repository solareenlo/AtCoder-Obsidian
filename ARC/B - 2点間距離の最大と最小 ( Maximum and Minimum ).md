# B - 2点間距離の最大と最小 ( Maximum and Minimum )
[[min-max]] [[Green]] [[ARC]] [[Go]]
#min-max #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc004/tasks/arc004_2

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)

	d := make([]int, n)
	maxi := 0
	for i := range d {
		fmt.Scan(&d[i])
		maxi += d[i]
	}
	sort.Ints(d)

	var mini int
	if len(d) == 0 {
		mini = 0
	} else {
		mini = max(0, d[n-1]-(maxi-d[n-1]))
	}

	fmt.Println(maxi)
	fmt.Println(mini)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```