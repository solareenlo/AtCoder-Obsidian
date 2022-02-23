# D - Binomial Coefficient is Fun
[[二項係数]] [[数列]] [[Yellow]] [[ARC]] [[Go]]
#二項係数 #数列 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc110/tasks/arc110_d

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, m int
	fmt.Fscan(in, &n, &m)

	sum := 0
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		sum += a
	}

	if m < sum {
		fmt.Println(0)
		return
	}

	x := 1
	y := 1
	for i := 1; i <= sum+n; i++ {
		x *= m + n - i + 1
		x %= mod
		y *= i
		y %= mod
	}
	fmt.Println(divMod(x, y))
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
```