# C - Sentou
[[min-max]] [[Gray]] [[ABC]] [[Go]]
#min-max #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc060/tasks/arc073_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, T int
	fmt.Scan(&n, &T)
	t := make([]int, n)
	for i := range t {
		fmt.Scan(&t[i])
	}

	res := 0
	for i := 0; i < n-1; i++ {
		res += min(t[i+1]-t[i], T)
	}
	res += T
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```