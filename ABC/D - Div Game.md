# D - Div Game
[[素因数]] [[素因数分解]] [[Brown]] [[ABC]] [[Go]]
#素因数 #素因数分解 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc169/tasks/abc169_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	pf := PrimeFactorization(n)

	cnt := 0
	for _, v := range pf {
		p := v
		b := 1
		for b <= p {
			p -= b
			b++
			cnt++
		}
	}
	fmt.Println(cnt)
}

func PrimeFactorization(n int) map[int]int {
	res := make(map[int]int)
	for i := 2; i*i <= n; i++ {
		for n%i == 0 {
			res[i]++
			n /= i
		}
	}
	if n != 1 {
		res[n]++
	}
	return res
}
```