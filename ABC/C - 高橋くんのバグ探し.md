# C - 高橋くんのバグ探し
[[DFS]] [[Green]] [[ABC]] [[Go]]
#DFS #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc015/tasks/abc015_3

## 解き方
```go
package main

import "fmt"

var n, k int
var t [5][5]int = [5][5]int{}

func dfs(num, val int) bool {
	if num == n {
		return val == 0
	}
	for i := 0; i < k; i++ {
		if dfs(num+1, t[num][i]^val) {
			return true
		}
	}
	return false
}

func main() {
	fmt.Scan(&n, &k)
	for i := 0; i < n; i++ {
		for j := 0; j < k; j++ {
			fmt.Scan(&t[i][j])
		}
	}
	if dfs(0, 0) {
		fmt.Println("Found")
	} else {
		fmt.Println("Nothing")
	}
}
```