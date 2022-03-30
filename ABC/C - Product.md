# C - Product
[[map]] [[Brown]] [[ABC]] [[Go]]
#map #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc233/tasks/abc233_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	ans := make(map[int]int)
	ans[1] = 1

	var n, x int
	fmt.Scan(&n, &x)

	for i := 0; i < n; i++ {
		m := make(map[int]int)
		var L int
		fmt.Scan(&L)
		for j := 0; j < L; j++ {
			var a int
			fmt.Scan(&a)
			for k, v := range ans {
				if k > x {
					continue
				}
				m[k*a] += v
			}
		}
		ans = m
	}
	fmt.Println(ans[x])
}
```