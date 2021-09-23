# B - Choose Integers
[[GCD]] [[Gray]] [[ABC]] [[Go]]
#GCD #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc060/tasks/abc060_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, c int
	fmt.Scan(&a, &b, &c)

	if c%gcd(a, b) != 0 {
		fmt.Println("NO")
	} else {
		fmt.Println("YES")
	}
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}
```