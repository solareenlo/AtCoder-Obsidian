# E - Integer Sequence Fair
[[数学的考察]] [[MOD]] [[Pow]] [[Light Blue]] [[ABC]] [[Go]]
#数学的考察 #MOD #Pow #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc228/tasks/abc228_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k, m int
	fmt.Scan(&n, &k, &m)

	mod := 998244353
	if m%mod != 0 {
		fmt.Println(powMod(m%mod, powMod(k%(mod-1), n, mod-1), mod))
	} else {
		fmt.Println(0)
	}
}

func powMod(a, n, mod int) int {
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