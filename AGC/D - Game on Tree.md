# D - Game on Tree
[[Grundy数]] [[xor]] [[DFS]] [[Yellow]] [[AGC]] [[Go]]
#Grundy数 #xor #DFS #Yellow #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc017/tasks/agc017_d

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var v = make([][]int, 100005)

func dfs(x, y int) int {
	ans := 0
	for _, t := range v[x] {
		if t != y {
			ans ^= dfs(t, x) + 1
		}
	}
	return ans
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	for i := 1; i < n; i++ {
		var x, y int
		fmt.Fscan(in, &x, &y)
		v[x] = append(v[x], y)
		v[y] = append(v[y], x)
	}

	if dfs(1, 0) != 0 {
		fmt.Println("Alice")
	} else {
		fmt.Println("Bob")
	}
}
```