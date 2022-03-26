# A - Ice Tea Store
[[偶奇]] [[Brown]] [[AGC]] [[Go]]
#偶奇 #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc019/tasks/agc019_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, c, d, n int
	fmt.Scan(&a, &b, &c, &d, &n)

	a = min(2*min(2*a, b), c)
	fmt.Println(n/2*min(a*2, d) + n%2*a)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```