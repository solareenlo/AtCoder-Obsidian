# C - Collinearity
[[全探索]] [[探索]] [[Gray]] [[ABC]] [[Go]]
#全探索 #探索 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc181/tasks/abc181_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	x := make([]int, n)
	y := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&x[i], &y[i])
	}

	for i := 0; i < n; i++ {
		for j := i + 1; j < n; j++ {
			for k := j + 1; k < n; k++ {
				dx := x[j] - x[i]
				dy := y[j] - y[i]
				if dx*(y[k]-y[i]) == dy*(x[k]-x[i]) {
					fmt.Println("Yes")
					return
				}
			}
		}
	}
	fmt.Println("No")
}
```