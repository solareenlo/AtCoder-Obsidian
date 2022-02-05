# C - Chocolate Bar
[[グリッド]] [[min-max]] [[Light Blue]] [[ARC]] [[Go]]
#グリッド #min-max #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc074/tasks/arc074_a

## 解き方
### Code
```go
package main

import "fmt"

func solve(w, h int) int {
	res := 1 << 60
	var a, b, c int
	for i := 1; i <= w; i++ {
		a = i * h
		b = (w - i) / 2 * h
		c = (w - i + 1) / 2 * h
		res = min(res, max(a, b, c)-min(a, b, c))
		b = (w - i) * (h / 2)
		c = (w - i) * ((h + 1) / 2)
		res = min(res, max(a, b, c)-min(a, b, c))
	}
	return res
}

func main() {
	var h, w int
	fmt.Scan(&h, &w)
	fmt.Println(min(solve(h, w), solve(w, h)))
}

func max(a ...int) int {
	res := a[0]
	for i := range a {
		if res < a[i] {
			res = a[i]
		}
	}
	return res
}

func min(a ...int) int {
	res := a[0]
	for i := range a {
		if res > a[i] {
			res = a[i]
		}
	}
	return res
}
```