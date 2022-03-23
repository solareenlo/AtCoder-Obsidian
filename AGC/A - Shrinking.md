# A - Shrinking
[[文字列]] [[シミュレーション]] [[Green]] [[AGC]] [[Go]]
#文字列 #シミュレーション #Green #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc016/tasks/agc016_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	ans := 100
	for i := 'a'; i <= 'z'; i++ {
		now := 0
		mx := 0
		for _, c := range s {
			if c == i {
				now = 0
			} else {
				now++
				mx = max(mx, now)
			}
		}
		ans = min(ans, mx)
	}
	fmt.Println(ans)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```