# C - Martial artist
[[BFS]] [[DFS]] [[Brown]] [[ABC]] [[Go]]
#BFS #DFS #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc226/tasks/abc226_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	t := make([]int, n)
	k := make([]int, n)
	e := make([][]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &t[i], &k[i])
		for j := 0; j < k[i]; j++ {
			var x int
			fmt.Fscan(in, &x)
			e[i] = append(e[i], x-1)
		}
	}

	used := make([]bool, n)
	used[n-1] = true
	res := 0
	for i := n - 1; i >= 0; i-- {
		if used[i] {
			res += t[i]
			for j := 0; j < k[i]; j++ {
				used[e[i][j]] = true
			}
		}
	}

	fmt.Println(res)
}
```