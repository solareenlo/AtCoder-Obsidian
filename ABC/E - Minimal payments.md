# E - Minimal payments
[[DFS]] [[Light Blue]] [[ABC]] [[Go]]
#DFS #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc231/tasks/abc231_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, x int
	fmt.Scan(&n, &x)

	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&a[i])
	}

	res := 0
	for i := n - 1; i >= 0; i-- {
		y := x % a[i]
		z := a[i] - y
		if z >= y || (y-z) < a[i-1] {
			res += x / a[i]
			x %= a[i]
		} else {
			res += x/a[i] + 1
			x = z
		}
	}
	fmt.Println(res)
}
```