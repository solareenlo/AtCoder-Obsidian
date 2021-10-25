# D - Triangles
[[sort]] [[二分探索]] [[lower_bound]] [[Brown]] [[ABC]] [[Go]]
#sort #二分探索 #lower_bound #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc143/tasks/abc143_d

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

	L := make([]int, n)
	for i := range L {
		fmt.Scan(&L[i])
	}
	sort.Ints(L)

	res := 0
	for i := 0; i < n; i++ {
		for j := 0; j < i; j++ {
			ab := L[i] + L[j]
			r := sort.SearchInts(L, ab)
			l := i + 1
			res += r - l
		}
	}

	fmt.Println(res)
}
```