# D - Binomial Coefficients
[[lower_bound]] [[Green]] [[ARC]] [[Go]]
#lower_bound #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc095/tasks/arc095_b

## 解き方
### Code lower_bound
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)
	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}
	sort.Ints(a)

	mid := a[n-1] / 2
	index := sort.SearchInts(a, mid)
	if a[index] == a[n-1] {
		fmt.Println(a[n-1], a[n-2])
	} else {
		if abs(mid-a[index]) <= abs(mid-a[index-1]) {
			fmt.Println(a[n-1], a[index])
		} else {
			fmt.Println(a[n-1], a[index-1])
		}
	}
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```
