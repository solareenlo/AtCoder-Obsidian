# D - ABS
[[数学的考察]] [[Light Blue]] [[ARC]] [[Go]]
#数学的考察 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc085/tasks/arc085_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, z, w int
	fmt.Scan(&n, &z, &w)

	a, b := 0, 0
	for i := 1; i <= n; i++ {
		fmt.Scan(&b)
		if i == n-1 || n == 1 {
			a = b
		}
	}
	fmt.Println(max(abs(w-b), abs(b-a)))
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
