# C - Ubiquity
[[MOD]] [[包摂原理]] [[Brown]] [[ABC]] [[Go]]
#MOD #包摂原理 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc178/tasks/abc178_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := 1
	b := 1
	c := 1
	mod := int(1e9 + 7)
	for i := 0; i < n; i++ {
		a = a * 10 % mod
		b = b * 9 % mod
		c = c * 8 % mod
	}

	fmt.Println(((a-2*b+c)%mod + mod) % mod)
}
```