# C - Sequence Scores
[[数列]] [[Pow]] [[inv]] [[MOD]] [[Yellow]] [[ARC]] [[Go]]
#数列 #Pow #inv #MOD #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc114/tasks/arc114_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var N, M int
	fmt.Scan(&N, &M)

	A := powMod(M, N-1)
	AM := A * M
	AN := A * N
	ans := AM * N
	for k := 0; k < M; k++ {
		D := invMod((M - k + mod) % mod)
		ans -= (((powMod(k, N)-AM+mod)%mod)*D%mod + AN) % mod * D % mod
		ans += mod
		ans %= mod
	}
	fmt.Println(ans)
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

func invMod(a int) int {
	return powMod(a, mod-2)
}
```