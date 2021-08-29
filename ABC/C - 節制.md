# C - 節制
[[二分探索]] [[sort]] [[Blue]] [[ABC]] [[Go]]
#二分探索 #sort #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc013/tasks/abc013_3

## 解き方
- 二分探索は `sort.Search` を用いる．

### Code 二分探索
```go
package main

import "fmt"

func main() {
	var n, h, a, b, c, d, e int
	fmt.Scan(&n, &h, &a, &b, &c, &d, &e)

	res := int(1e16)
	for i := 0; i <= n; i++ {
		l, r := -1, n-i
		for r-l > 1 {
			m := (l + r) / 2
			x := h + b*i + d*m - (n-i-m)*e
			if x > 0 {
				r = m
			} else {
				l = m
			}
		}
		res = min(res, a*i+c*r)
	}
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code sort
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, h, a, b, c, d, e int
	fmt.Scan(&n, &h, &a, &b, &c, &d, &e)
	res := int(1e16)
	for i := 0; i <= n; i++ {
		j := sort.Search(n-i, func(j int) bool {
			return h+b*i+d*j-(n-i-j)*e > 0
		})
		res = min(res, a*i+c*j)
	}
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```