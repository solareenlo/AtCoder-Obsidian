# E - Everything on It
[[包除原理]] [[DP]] [[Red]] [[ARC]] [[Go]]
#包除原理 #DP #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc096/tasks/arc096_c

## 解き方
### Code
```go
package main

import "fmt"

func Pow(a, b, mod int) int {
	s := 1
	for ; b > 0; b >>= 1 {
		if b&1 != 0 {
			s = s * a % mod
		}
		a = a * a % mod
	}
	return s
}

func main() {
	var n, mod int
	fmt.Scan(&n, &mod)

	c := [3003][3003]int{}
	g := [3003][3003]int{}
	for i := 0; i <= n; i++ {
		c[i][0] = 1
		g[i][0] = 1
		for j := 1; j <= i; j++ {
			c[i][j] = (c[i-1][j-1] + c[i-1][j]) % mod
			g[i][j] = (g[i-1][j-1] + (j+1)*g[i-1][j]) % mod
		}
	}

	ans := 0
	for i := 0; i <= n; i++ {
		s := 0
		x := Pow(2, n-i, mod)
		pw := 1
		for j := 0; j <= i; j++ {
			s = (s + g[i][j]*pw) % mod
			pw = pw * x % mod
		}
		tmp := 1
		if i&1 != 0 {
			tmp = -1
		}
		ans = (ans + tmp*c[n][i]*s%mod*Pow(2, Pow(2, n-i, mod-1), mod)) % mod
	}

	fmt.Println((ans + mod) % mod)
}
```