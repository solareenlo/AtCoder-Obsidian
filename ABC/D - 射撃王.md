# D - 射撃王
[[二分探索]] [[sort]] [[Light Blue]] [[ABC]] [[Go]]
#二分探索 #sort #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc023/tasks/abc023_d

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

	h, s := make([]int, n), make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&h[i], &s[i])
	}

	r, l := 1<<60, 0
	for r-l > 1 {
		m := (r + l) / 2
		ok := true
		t := make([]int, n)
		for i := 0; i < n; i++ {
			if m < h[i] {
				ok = false
			} else {
				t[i] = (m - h[i]) / s[i]
			}
		}
		sort.Ints(t)
		for i := 0; i < n; i++ {
			if i > t[i] {
				ok = false
			}
		}
		if ok {
			r = m
		} else {
			l = m
		}
	}
	fmt.Println(r)
}
```