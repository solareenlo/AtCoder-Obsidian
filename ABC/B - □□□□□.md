# B - □□□□□
[[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc040/tasks/abc040_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res := 100100100
	for i := 1; i*i <= n; i++ {
		j := n / i
		res = min(res, abs(i-j)+n-i*j)
	}
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```