# E - Digit Products
[[メモ化再帰]] [[再帰関数]] [[Yellow]] [[ABC]] [[Go]]
#メモ化再帰 #再起関数 #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc208/tasks/abc208_e

## 解き方
### Code メモ化再帰
```go
package main

import "fmt"

var (
	n, k int
	m    = map[pair]int{}
)

type pair struct{ n, k int }

func f(n, k int) int {
	if _, ok := m[pair{n, k}]; ok {
		return m[pair{n, k}]
	}
	r := n / 10
	if k > 0 {
		r += 1
	}
	for i := 1; i < min(9, n)+1; i++ {
		r += f((n-i)/10, k/i)
	}
	m[pair{n, k}] = r
	return r
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func main() {
	fmt.Scan(&n, &k)
	fmt.Println(f(n, k) - 1)
}
```