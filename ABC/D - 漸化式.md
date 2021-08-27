# D - 漸化式
[[Matrix]] [[xor]] [[Pow]] [[漸化式]] [[Yellow]] [[ABC]] [[Go]]
#Matrix #xor #Pow #漸化式 #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc009/tasks/abc009_4

## 解き方
- 行列の足し算は `xor`
- 行列の掛け算は `and`

### Code
```go
package main

import "fmt"

func main() {
	var k, m int
	fmt.Scan(&k, &m)

	A := make([]int, k)
	for i := range A {
		fmt.Scan(&A[i])
	}
	if m <= k {
		fmt.Println(A[m-1])
		return
	}

	c := make([]int, k)
	for i := range c {
		fmt.Scan(&c[i])
	}

	b := make([][]int, k)
	for i := range b {
		b[i] = make([]int, k)
	}
	for i := 0; i < k-1; i++ {
		b[i][i+1] = 1<<32 - 1
	}
	for i := 0; i < k; i++ {
		b[k-1][i] = c[k-1-i]
	}

	a := make([][]int, k)
	for i := 0; i < k; i++ {
		a[i] = []int{A[i]}
	}

	res := mul(pow(b, m-k), a)
	fmt.Println(res[k-1][0])
}

func mul(a, b [][]int) [][]int {
	res := make([][]int, len(a))
	for i := 0; i < len(a); i++ {
		res[i] = make([]int, len(b))
	}
	for i := 0; i < len(a); i++ {
		for j := 0; j < len(b); j++ {
			for k := 0; k < len(b[0]); k++ {
				res[i][k] ^= a[i][j] & b[j][k]
			}
		}
	}
	return res
}

func pow(a [][]int, n int) [][]int {
	res := make([][]int, len(a))
	for i := 0; i < len(a); i++ {
		res[i] = make([]int, len(a))
		res[i][i] = 1<<32 - 1
	}
	for n > 0 {
		if n&1 == 1 {
			res = mul(res, a)
		}
		a = mul(a, a)
		n >>= 1
	}
	return res
}
```