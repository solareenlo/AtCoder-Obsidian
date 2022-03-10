# F - Square
[[グリッド]] [[DP]] [[bitDP]] [[Orange]] [[ARC-Like]] [[Go]]
#グリッド #DP #bitDP #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/caddi2018/tasks/caddi2018_d

## 解き方
### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

const MOD = 998244353

var (
	n int
	M = map[int]int{}
	u int
	d = [100005]int{}
)

func check(a, b int) int {
	if a == b {
		return 0
	}
	return 1
}

func as(a, b, c int) {
	t := a*n + b
	k := check(M[t], c)
	if M[t] == 0 {
		M[t] = c
		if M[t] != 0 {
			u++
		}
	} else if a == 2 {
		as(0, b+1, k+1)
	} else if a == 1 {
		d[b] = k + 1
	} else if k != 0 {
		fmt.Println(0)
		os.Exit(0)
	}
}

func exp(b, n int) int {
	res := 1
	for ; n > 0; n /= 2 {
		if n%2 != 0 {
			res *= b
			res %= MOD
		}
		b *= b
		b %= MOD
	}
	return res
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var m int
	fmt.Fscan(in, &n, &m)

	for i := 0; i < m; i++ {
		var a, b, c int
		fmt.Fscan(in, &a, &b, &c)
		if a < b {
			a, b = b, a
		}
		as(a-b, b-1, c+1)
	}

	for i := 0; i < n; i++ {
		if d[i] != 0 && M[i] != 0 {
			as(0, i+1, check(M[i], d[i])+1)
			d[i] = 0
		}
	}

	for i := n - 2; i >= 0; i-- {
		if d[i] != 0 && M[i+1] != 0 {
			as(0, i, check(M[i+1], d[i])+1)
			d[i] = 0
		}
	}

	for i := 0; i < n; i++ {
		if d[i] != 0 {
			u++
		}
	}
	fmt.Println(exp(2, n*(n+1)/2-u))
}
```

### Code DP Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var N, M int
	fmt.Fscan(in, &N, &M)
	A := make([]int, N+1)
	for i := range A {
		A[i] = -1
	}

	const mod = 998244353
	pow2 := [100005]int{}
	pow2[0] = 1
	for i := 1; i <= N; i++ {
		pow2[i] = (pow2[i-1] * 2) % mod
	}

	Mp := make([]map[int]int, 100005)
	for i := range Mp {
		Mp[i] = map[int]int{}
	}
	for i := 0; i < M; i++ {
		var a, b, c int
		fmt.Fscan(in, &a, &b, &c)
		if a == b {
			A[a] = c
			continue
		}
		if b < a {
			a, b = b, a
		}
		if _, ok := Mp[a][b]; ok {
			Mp[a][b] = ((c + Mp[a][b]) % 2) - 2
		} else {
			Mp[a][b] = c
		}
	}
	dp0 := 0
	dp1 := 0
	if A[N] == -1 || A[N] == 1 {
		dp1 = 1
	}
	if A[N] == -1 || A[N] == 0 {
		dp0 = 1
	}
	for i := N - 1; 1 <= i; i-- {
		Size := len(Mp[i])
		X := pow2[N-i-Size]
		x00 := X
		x01 := X
		x10 := X
		x11 := X
		for v, c := range Mp[i] {
			if 0 <= c {
				continue
			}
			if v == i+1 {
				if c != -2 {
					x00 = 0
					x11 = 0
				} else {
					x10 = 0
					x01 = 0
				}
			} else if v == i+2 {
				if c == -2 {
					x11 = 0
					x01 = 0
				} else {
					x00 = 0
					x10 = 0
				}
			} else {
				if c != -2 {
					x01 = 0
					x11 = 0
					x00 = 0
					x10 = 0
				}
			}
		}
		d1 := (x11*dp1 + x10*dp0) % mod
		d0 := (x01*dp1 + x00*dp0) % mod
		dp1 = d1
		dp0 = d0
		if A[i] == 1 {
			dp0 = 0
		}
		if A[i] == 0 {
			dp1 = 0
		}
	}
	fmt.Println((dp1 + dp0) % mod)
}
```