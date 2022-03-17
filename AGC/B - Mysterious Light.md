# B - Mysterious Light
[[GCD]] [[Gray]] [[AGC]] [[Go]]
#GCD #Gray #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc001/tasks/agc001_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	fmt.Println(3 * (n - gcd(n, m)))
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}
```