# C - Triangle?
[[図形]] [[面積]] [[全探索]] [[Gray]] [[ABC]] [[Go]]
#図形 #面積 #全探索 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc224/tasks/abc224_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	x := make([]int, 303)
	y := make([]int, 303)
	for i := 0; i < n; i++ {
		fmt.Scan(&x[i], &y[i])
	}

	res := 0
	for i := 0; i < n-2; i++ {
		for j := i + 1; j < n-1; j++ {
			for k := j + 1; k < n; k++ {
				if (x[j]-x[i])*(y[k]-y[i])-(x[k]-x[i])*(y[j]-y[i]) != 0 {
					res++
				}
			}
		}
	}
	fmt.Println(res)
}
```