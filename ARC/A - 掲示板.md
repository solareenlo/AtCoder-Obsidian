# A - 掲示板
[[map]] [[Green]] [[ARC]] [[Go]]
#map #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc042/tasks/arc042_a

## 解き方
### Code
```go
package main

import (
	"fmt"
)

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	a := make([]int, m)
	for i := m - 1; i >= 0; i-- {
		fmt.Scan(&a[i])
	}

	res := map[int]bool{}
	for i := 0; i < m; i++ {
		if !res[a[i]] {
			fmt.Println(a[i])
			res[a[i]] = true
		}
	}

	for i := 1; i < n+1; i++ {
		if !res[i] {
			fmt.Println(i)
		}
	}
}
```