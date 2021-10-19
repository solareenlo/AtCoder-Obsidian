# F - Frog Jump
[[TLE]] [[数学的考察]] [[Orange]] [[ABC]] [[Go]]
#TLE #数学的考察 #Orange #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc128/tasks/abc128_f

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	s := make([]int, n)
	for i := range s {
		fmt.Scan(&s[i])
	}

	maxi := -(1 << 60)
	for i := 1; i < n; i++ {
		now := 0
		l, r := 0, n-1
		for r > i && (r%i != 0 || l < r) {
			now += s[l] + s[r]
			maxi = max(maxi, now)
			l += i
			r -= i
		}
	}
	fmt.Println(maxi)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```