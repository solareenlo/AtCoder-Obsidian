# C - Select Mul
[[全探索]] [[bit全探索]] [[Gray]] [[ABC]] [[Go]]
#全探索 #bit全探索 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc221/tasks/abc221_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	n := make([]byte, 0)
	fmt.Scan(&n)

	sort.Slice(n, func(i, j int) bool {
		return n[i] > n[j]
	})

	res := 0
	for bit := 0; bit < 1<<len(n); bit++ {
		l, r := 0, 0
		for i := 0; i < len(n); i++ {
			if bit&(1<<i) != 0 {
				l = l*10 + int(n[i]-'0')
			} else {
				r = r*10 + int(n[i]-'0')
			}
		}
		res = max(res, l*r)
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```