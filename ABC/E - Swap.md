# E - Swap
[[文字列]] [[DFS]] [[Yellow]] [[ABC]] [[Go]]
#文字列 #DFS #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc227/tasks/abc227_e

## 解き方
### Code
```go
package main

import "fmt"

type pair struct {
	s string
	k int
}

var (
	m   = map[pair]int{}
	KEY = "KEY"
)

func dfs(s string, k int) int {
	n := len(s)
	if k < 0 {
		return 0
	}
	if k == 0 || n <= 1 {
		return 1
	}
	t := m[pair{s, k}]
	if t != 0 {
		return t
	}
	sum := 0
	for i := 0; i < 3; i++ {
		for j := 0; j < n; j++ {
			if KEY[i] == s[j] {
				sum += dfs(s[:j]+s[j+1:], k-j)
				break
			}
		}
	}
	m[pair{s, k}] = sum
	return sum
}

func main() {
	var s string
	var k int
	fmt.Scan(&s, &k)
	fmt.Println(dfs(s, k))
}
```