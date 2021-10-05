# D - Practical Skill Test
[[グリッド]] [[累積和]] [[Green]] [[ABC]] [[Go]]
#グリッド #累積和 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc089/tasks/abc089_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var h, w, d int
	fmt.Scan(&h, &w, &d)
	x, y := make([]int, h*w+1), make([]int, h*w+1)
	var a int
	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			fmt.Scan(&a)
			x[a] = j
			y[a] = i
		}
	}

	s := make([]int, h*w+1)
	for i := 0; i < h*w-d+1; i++ {
		s[i+d] = s[i] + abs(x[i+d]-x[i]) + abs(y[i+d]-y[i])
	}

	var q, l, r int
	fmt.Scan(&q)
	for i := 0; i < q; i++ {
		fmt.Scan(&l, &r)
		fmt.Println(s[r] - s[l])
	}
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```