# C - Grand Garden
[[区間]] [[数学的考察]] [[Brown]] [[ABC]] [[Go]]
#区間 #数学的考察 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc116/tasks/abc116_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	h := make([]int, n)
	sum := 0
	for i := range h {
		fmt.Scan(&h[i])
		sum += h[i]
	}

	cnt := 0
	for sum > 0 {
		l := 0
		for i := 0; i < n; i++ {
			if h[i] > 0 {
				l = i
				break
			}
		}

		r := l
		for i := l + 1; i < n; i++ {
			if h[i] != 0 {
				r = i
			} else {
				break
			}
		}

		for i := l; i <= r; i++ {
			h[i]--
		}

		cnt++
		sum = 0
		for i := 0; i < n; i++ {
			sum += h[i]
		}
	}
	fmt.Println(cnt)
}
```