# A - 鉛筆リサイクルの新技術
[[Brown]] [[ARC]] [[Go]]
#Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc011/tasks/arc011_1

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var m, n, N int
	fmt.Scan(&m, &n, &N)

	sale := N
	notSale := 0
	for (sale+notSale)/m > 0 {
		div := (sale + notSale) / m
		rem := (sale + notSale) % m
		notSale = 0
		sale = div * n
		notSale = rem
		N += sale
	}

	fmt.Println(N)
}
```