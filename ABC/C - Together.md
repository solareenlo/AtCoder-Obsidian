# C - Together
[[map]] [[Gray]] [[ABC]] [[Go]]
#map #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc072/tasks/arc082_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	m := map[int]int{}
	var t int
	for i := 0; i < n; i++ {
		fmt.Scan(&t)
		m[t]++
		m[t-1]++
		m[t+1]++
	}

	res := 0
	for i := range m {
		res = max(res, m[i])
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