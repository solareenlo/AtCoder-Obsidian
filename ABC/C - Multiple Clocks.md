# C - Multiple Clocks
[[GCD]] [[Brown]] [[ABC]] [[Go]]
#GCD #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc070/tasks/abc070_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	var res, t int
	fmt.Scan(&res)
	for i := 0; i < n-1; i++ {
		fmt.Scan(&t)
		g := gcd(res, t)
		res /= g
		res *= t
	}
	fmt.Println(res)
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}
```