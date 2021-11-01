# D - Bouquet
[[nCr]] [[繰り返し二乗法]] [[Green]] [[ABC]] [[Go]]
#nCr #繰り返し二乗法 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc156/tasks/abc156_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)

	res := powMod(2, n) - 1 - nCrMod(n, a) - nCrMod(n, b)
	res %= mod
	res += mod
	res %= mod

	fmt.Println(res)

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

func invMod(a int) int {
	return powMod(a, mod-2)
}

func nCrMod(n, r int) int {
	if n < r || n < 0 || r < 0 {
		return 0
	}
	res := 1
	for i := 0; i < r; i++ {
		res = res * (n - i) % mod
		res = res * invMod(i+1) % mod
	}
	return res
}
```