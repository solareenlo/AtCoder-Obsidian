# D - Xor Sum
[[DFS]] [[Orange]] [[ARC]] [[Go]]
#DFS #Orange #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc066/tasks/arc066_b

## 解き方
### Code
```go
package main

import "fmt"

const mod = 1_000_000_007

var (
	s = map[int]int{}
	n int
)

func dfs(n int) int {
	if n == 0 || n == 1 {
		return n + 1
	}
	if s[n] != 0 {
		return s[n]
	}
	s[n] = (dfs(n/2) + dfs(n/2-1) + dfs((n-1)/2)) % mod
	return s[n]
}

func main() {
	fmt.Scan(&n)
	fmt.Println(dfs(n))
}
```