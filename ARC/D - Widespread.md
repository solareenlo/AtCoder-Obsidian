# D - Widespread
[[二分探索]] [[Light Blue]] [[ARC]] [[Go]]
#二分探索 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc075/tasks/arc075_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)
	s := make([]int, n)
	for i := range s {
		fmt.Scan(&s[i])
	}

	l, r := 0, int(1e9)
	for r-l > 1 {
		m, t := (r+l)/2, 0
		for i := 0; i < n; i++ {
			t += (max(s[i]-b*m, 0) + a - b - 1) / (a - b)
		}
		if t <= m {
			r = m
		} else {
			l = m
		}
	}
	fmt.Println(r)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```