# D - Chaotic Polygons
[[数学的考察]] [[図形]] [[Yellow]] [[ARC]] [[Go]]
#数学的考察 #図形 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc037/tasks/arc037_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	ans := 1
	h := 2
	f := 1
	mod := 1_000_000_007
	for i := 0; i < n; i++ {
		ans = ans*3 + h*h%mod*h
		ans %= mod
		d := (h + f) * (h - f) % mod
		f *= d
		f %= mod
		h *= h + d
		h %= mod
	}

	fmt.Println((ans + mod) % mod)
}
```