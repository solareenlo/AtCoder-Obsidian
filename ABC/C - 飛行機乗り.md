# C - 飛行機乗り
[[lower_bound]] [[Green]] [[ABC]] [[Go]]
#lower_bound #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc030/tasks/abc030_c

## 解き方
- `lower_bound` = `sort.SearchInts`

### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, m, x, y int
	fmt.Scan(&n, &m, &x, &y)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}
	b := make([]int, m)
	for i := range b {
		fmt.Scan(&b[i])
	}

	cnt, now := 0, 0
	for {
		i := sort.SearchInts(a, now)
		if i >= n {
			break
		}
		now = a[i] + x
		i = sort.SearchInts(b, now)
		if i >= m {
			break
		}
		cnt++
		now = b[i] + y
	}
	fmt.Println(cnt)
}
```