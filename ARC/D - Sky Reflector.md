# D - Sky Reflector
[[Pow]] [[MOD]] [[Light Blue]] [[ARC]] [[Go]]
#Pow #MOD #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc113/tasks/arc113_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m, k int
	fmt.Scan(&n, &m, &k)

	a := 0
	if n == 1 || m == 1 {
		a = powMod(k, n*m)
	} else {
		for i := 0; i < k; i++ {
			a += (powMod(i+1, n) - powMod(i, n) + mod) % mod * powMod(-i+k, m) % mod
			a %= mod
		}
	}
	fmt.Println(a)
}

const mod = 998244353

func powMod(a, n int) int {
	res := 1
	for n > 0 {
		if n%2 == 1 {
			res = res * a % mod
		}
		a = a * a % mod
		n /= 2
	}
	return res
}
```