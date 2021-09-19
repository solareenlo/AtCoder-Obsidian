# C - Scc Puzzle
[[パターン]] [[Gray]] [[ABC]] [[Go]]
#パターン #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc055/tasks/arc069_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	res := m / 2
	if 2*n < m {
		res = n + ((m - 2*n) / 4)
	}
	fmt.Println(res)
}
```