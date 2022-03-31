# E - Arithmetic Number
[[等差数列]] [[Green]] [[ABC]] [[Go]]
#等差数列 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc234/tasks/abc234_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x int
	fmt.Scan(&x)

	ans := 1 << 60
	for i := 0; i < 10; i++ {
		for j := 0; j < 10; j++ {
			d := j - i
			e := i
			y := 0
			for k := 0; k < 18; k++ {
				if e < 0 || e > 9 {
					break
				}
				y = y*10 + e
				e += d
				if y >= x {
					ans = min(ans, y)
				}
			}
		}
	}
	fmt.Println(ans)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```