# D - 数直線
[[lower_bound]] [[二分探索]] [[Black]] [[Others]] [[Go]]
#lower_bound #二分探索 #Black #Others #Go

## 問題
- https://atcoder.jp/contests/bcu30/tasks/bcu30_d

## 解き方
- C++ でいうところの `lower_bound` を使う
- Go には `lower_bound` がないので，二分探索ができる `sort.Search` を使う
- [func Search](https://golang.org/pkg/sort/#Search)

### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, q int
	fmt.Scan(&n, &q)

	var x = make([]int, n)
	var s = make([]int, n+1)
	for i := 0; i < n; i++ {
		fmt.Scan(&x[i])
		s[i+1] = s[i] + x[i]
	}
	sort.Ints(x)

	for i := 0; i < q; i++ {
		var t int
		fmt.Scan(&t)
		m := sort.Search(len(x), func(i int) bool { return t < x[i] })
		fmt.Println(s[n]-s[m]-t*(n-m)+t*m-s[m])
	}
}
```