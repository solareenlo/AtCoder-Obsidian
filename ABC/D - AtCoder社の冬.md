# D - AtCoder社の冬
[[MOD]] [[inv]] [[Yellow]] [[ABC]] [[Go]]
#MOD #inv #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc003/tasks/abc003_4

## 解き方
### Code inv
```go
package main

import "fmt"

var mod int = 1e9 + 7
var r, c, x, y, d, l int

func pow(a, b int) int {
	if b == 0 {
		return 1
	}
	if b%2 == 1 {
		return pow(a, b-1) * a % mod
	}
	c := pow(a, b/2)
	return c * c % mod
}

func comb(a, b int) int {
	n, m := 1, 1
	for i := a - b + 1; i <= a; i++ {
		n = n * i % mod
	}
	for i := 1; i <= b; i++ {
		m = m * i % mod
	}
	return n * pow(m, mod-2) % mod
}

func a(x, y int) int {
	if x <= 0 || y <= 0 {
		return 0
	}
	if x*y < d+l {
		return 0
	}
	return comb(x*y, d) * comb(x*y-d, l) % mod
}

func main() {
	fmt.Scan(&r, &c, &x, &y, &d, &l)
	fmt.Println((r - x + 1) * (c - y + 1) % mod * ((a(x, y) - (a(x, y-1)+a(x-1, y))*2%mod + (a(x-1, y-1)*4+a(x-2, y)+a(x, y-2))%mod - (a(x-2, y-1)+a(x-1, y-2))*2%mod + a(x-2, y-2) + mod*3) % mod) % mod)
}
```

### Code
```go
package main

import "fmt"

var mod int = 1e9 + 7
var p [1001][1001]int = [1001][1001]int{}
var r, c, x, y, d, l int

func f(a, b int) int {
	if a >= 0 && b >= 0 {
		return p[a*b][d+l]
	}
	return 0
}

func main() {
	p[0][0] = 1
	for i := 1; i < 1000; i++ {
		p[i][0] = 1
		p[i][i] = 1
		for j := 1; j < i; j++ {
			p[i][j] = (p[i-1][j-1] + p[i-1][j]) % mod
		}
	}
	fmt.Scan(&r, &c, &x, &y, &d, &l)
	res := (f(x, y) - (2*f(x-1, y) + 2*f(x, y-1)) + (4*f(x-1, y-1) + f(x-2, y) + f(x, y-2)) - (2*f(x-2, y-1) + 2*f(x-1, y-2)) + f(x-2, y-2)) % mod
	res = (res + mod) % mod
	res = res * (r - x + 1) % mod * (c - y + 1) % mod * p[d+l][d] % mod
	fmt.Println(res)
}
```