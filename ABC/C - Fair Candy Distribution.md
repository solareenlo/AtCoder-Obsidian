# C - Fair Candy Distribution
[[sort]] [[数学的考察]] [[Gray]] [[ABC]]
#sort #数学的考察 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc208/tasks/abc208_c

## 解き方
### Code sort
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	var a = make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&a[i])
	}

	var b = make([]int, n)
	copy(b, a)
	sort.Ints(b)

	m := k/n
	for i := 0; i < n; i++ {
		if a[i] < b[k-n*m] {
			fmt.Println(m + 1)
		} else {
			fmt.Println(m)
		}
	}
}
```