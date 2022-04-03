# Ex - Dice Product 2
[[乗法的関数]] [[DP]] [[期待値]] [[Orange]] [[ABC]] [[Go]]
#乗法的関数 #DP #期待値 #Orange #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc239/tasks/abc239_h

## 解き方

### Code 乗法的関数
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	const S = 180180

	var n, m int
	fmt.Scan(&n, &m)
	rev := powMod(n-1, mod-2)
	g := make([]int, S*2+1)
	f := make([]int, S*2+1)
	for i := 1; i < S+1; i++ {
		g[i] = (g[i] + g[i-1]) % mod
		f[i] = (g[i] + n) * rev % mod
		if f[i] < 0 {
			f[i] += mod
		}
		for j := 2; j < min(n, S/i)+1; j++ {
			g[i*j] += f[i]
			g[i*j+j] -= f[i]
		}
	}

	h := make([]int, S)
	LIM := m / S
	for d := m / S; d >= 1; d-- {
		M := m / d
		h[d] = n
		sqM := int(math.Floor(math.Sqrt(float64(M))))
		Go := M / 2
		en := M/(M/2) - 1
		for i := 2; i <= min(M, n); i++ {
			if i > sqM+3 {
				Go--
			} else {
				Go = M / i
			}
			if i < sqM-3 {
				en++
			} else {
				en = M / Go
			}
			if en > n {
				en = n
			}
			if d*i <= LIM {
				h[d] += (en - i + 1) * h[d*i]
			} else {
				h[d] += (en - i + 1) * f[Go]
			}
			i = en
		}
		h[d] = h[d] % mod * rev % mod
	}

	if m < S {
		fmt.Println(f[m])
	} else {
		fmt.Println(h[1])
	}
}

const mod = 1000000007

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

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var N, M int
	fmt.Scan(&N, &M)

	high := make([]int, 50000)
	low := make([]int, 50000)
	L := int(math.Round(math.Sqrt(float64(M))))
	K := M / (L + 1)
	for i := 1; i <= L+K; i++ {
		x := M / (L + K + 1 - i)
		if i <= L {
			x = i
		}
		sum := 0
		for l, r, le := 2, 0, min(N, x); l <= le; l = r {
			q := x / l
			r = min(N, x/q) + 1
			var cur int
			if q <= L {
				cur = low[q]
			} else {
				cur = high[M/q]
			}
			sum += cur * (r - l) % mod
			sum %= mod
		}
		if i <= L {
			low[i] = divMod(sum+N%mod, N-1)
		} else {
			high[L+K+1-i] = divMod(sum+N%mod, N-1)
		}
	}

	if M <= L {
		fmt.Println(low[M])
	} else {
		fmt.Println(high[1])
	}
}

const mod = 1000000007

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

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```