# F - Do you like query problems?
[[期待値]] [[Pow]] [[div]] [[MOD]] [[Red]] [[Go]]
#期待値 #Pow #div #MOD #Red #Go 

## 問題
- https://atcoder.jp/contests/arc111/tasks/arc111_f

## 解き方

### Code2
```go
package main

import "fmt"

func main() {
	var N, M, Q int
	fmt.Scan(&N, &M, &Q)

	C := divMod((2*M+1)%mod*N%mod*(N+1)%mod, 2)
	CQ := powMod(C, Q-1)
	ans := CQ * Q % mod * divMod(M*(M-1)%mod, 2) % mod * divMod(N*(N+1)%mod*(N+2)%mod, 6) % mod
	ret := CQ * C % mod * N % mod
	for i := 0; i < N; i++ {
		tmp := C - (M * (i + 1) % mod * (N - i) % mod)
		tmp += mod
		tmp %= mod
		ret -= powMod(tmp, Q)
		ret += mod
		ret %= mod
	}
	tmp := divMod(ret*(M-1)%mod, 2)
	ans = divMod(((ans-tmp)+mod)%mod, M)
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

func divMod(a, b int) int {
	ret := a * modInv(b)
	ret %= mod
	return ret
}

func modInv(a int) int {
	b, u, v := mod, 1, 0
	for b != 0 {
		t := a / b
		a -= t * b
		a, b = b, a
		u -= t * v
		u, v = v, u
	}
	u %= mod
	if u < 0 {
		u += mod
	}
	return u
}
```

### Code1
```go
package main

import "fmt"

func main() {
	var n, m, q int
	fmt.Scan(&n, &m, &q)

	res := 0
	t := powMod(n*(n+1)*(2*m+1)%mod, mod-2)
	for i := 1; i <= n; i++ {
		pi := 2 * i * (n - i + 1) % mod * t % mod * m % mod
		s := (q - (1-powMod(1-pi+mod, q)+mod)*powMod(pi, mod-2)%mod + mod) % mod
		res = (res + t*(m-1)%mod*i%mod*(n-i+1)%mod*s) % mod
	}

	iv2 := (mod + 1) / 2
	fmt.Println(res * powMod(n*(n+1)%mod*iv2%mod*(2*m+1)%mod, q) % mod)
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