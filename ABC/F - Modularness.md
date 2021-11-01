# F - Modularness
[[MOD]] [[数学的考察]] [[Yellow]] [[ABC]] [[Go]]
#MOD #数学的考察 #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc156/tasks/abc156_f

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var k, q int
	fmt.Scan(&k, &q)

	d := make([]int, k)
	for i := range d {
		fmt.Scan(&d[i])
	}

	for i := 0; i < q; i++ {
		var n, x, m int
		fmt.Scan(&n, &x, &m)
		a := x % m
		for j := 0; j < k; j++ {
			a += ((d[j]+m-1)%m + 1) * ((n - 2 + k - j) / k)
		}
		fmt.Println(n - 1 - a/m)
	}
}
```