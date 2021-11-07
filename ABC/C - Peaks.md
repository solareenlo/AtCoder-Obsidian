# C - Peaks
[[DFS]] [[Gray]] [[ABC]] [[Go]]
#DFS #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc166/tasks/abc166_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	h := make([]int, n)
	for i := range h {
		fmt.Scan(&h[i])
	}

	ok := make([]bool, n)
	for i := 0; i < n; i++ {
		ok[i] = true
	}

	for i := 0; i < m; i++ {
		var a, b int
		fmt.Scan(&a, &b)
		a--
		b--
		if h[a] <= h[b] {
			ok[a] = false
		}
		if h[b] <= h[a] {
			ok[b] = false
		}
	}

	cnt := 0
	for i := 0; i < n; i++ {
		if ok[i] {
			cnt++
		}
	}
	fmt.Println(cnt)
}
```