# E - Sum of gcd of Tuples (Hard)
[[MOD]] [[Pow]] [[数学的考察]] [[Blue]] [[ABC]] [[Go]]
#MOD #Pow #数学的考察 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc162/tasks/abc162_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	pow := make([]int, k+1)
	res := 0
	for i := k; i >= 1; i-- {
		pow[i] = powMod(k/i, n)
		for j := 2 * i; j <= k; j += i {
			pow[i] -= pow[j]
			pow[i] += mod
			pow[i] %= mod
		}
		res += pow[i] * i % mod
		res %= mod
	}

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
```