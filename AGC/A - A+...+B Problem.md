# A - A+...+B Problem
[[min-max]] [[Brown]] [[AGC]] [[Go]]
#min-max #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc015/tasks/agc015_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)

	fmt.Println(max(0, (n-2)*(b-a)+1))
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```