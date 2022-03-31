# C - Happy New Year!
[[DFS]] [[10進数]] [[Gray]] [[ABC]] [[Go]]
#DFS #10進数 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc234/tasks/abc234_c

## 解き方
### Code
```go
package main

import "fmt"

func dfs(x int) {
	if x == 0 {
		return
	}
	dfs(x / 2)
	fmt.Print((x % 2) * 2)
}

func main() {
	var x int
	fmt.Scan(&x)
	dfs(x)
}
```