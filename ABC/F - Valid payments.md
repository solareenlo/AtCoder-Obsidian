# F - Valid payments
[[数学的考察]] [[DP]] [[Yellow]] [[ABC]] [[Go]]
#数学的考察 #DP #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc182/tasks/abc182_f

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, X, A int
	fmt.Scan(&n, &X, &A)
	a, b := 0, 1
	h := X

	n--
	for i := 0; i < n; i++ {
		fmt.Scan(&A)
		c := a + b
		if h%A != 0 {
			a = c
		}
		if X%A != 0 {
			b = c
		}
		X = (X / A) * A
		h = ((h + A - 1) / A) * A
	}

	fmt.Println(a + b)
}
```