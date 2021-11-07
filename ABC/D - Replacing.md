# D - Replacing
[[map]] [[数列]] [[Brown]] [[ABC]] [[Go]]
#map #数列 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc171/tasks/abc171_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := map[int]int{}
	sum := 0
	for i := 0; i < n; i++ {
		tmp := 0
		fmt.Scan(&tmp)
		sum += tmp
		a[tmp]++
	}

	var q int
	fmt.Scan(&q)
	for i := 0; i < q; i++ {
		var b, c int
		fmt.Scan(&b, &c)
		if _, ok := a[b]; ok {
			sum += a[b] * (c - b)
			a[c] += a[b]
			a[b] = 0
		}
		fmt.Println(sum)
	}
}
```