# C - Pyramid
[[全探索]] [[探索]] [[Green]] [[ABC]] [[Go]]
#全探索 #探索 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc112/tasks/abc112_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	x, y, h := make([]int, n), make([]int, n), make([]int, n)
	var t int
	for i := 0; i < n; i++ {
		fmt.Scan(&x[i], &y[i], &h[i])
		if h[i] > 0 {
			t = i
		}
	}

	for cy := 0; cy < 101; cy++ {
		for cx := 0; cx < 101; cx++ {
			ch := max(h[t]+abs(x[t]-cx)+abs(y[t]-cy), 0)
			ok := true
			for i := 0; i < n; i++ {
				tmp := max(ch-abs(x[i]-cx)-abs(y[i]-cy), 0)
				if h[i] != tmp {
					ok = false
				}
			}
			if ok {
				fmt.Println(cx, cy, ch)
				return
			}
		}
	}
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```