# C - Boxes and Candies
[[数列]] [[数学的考察]] [[Green]] [[ABC]] [[Go]]
#数列 #数学的考察 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc048/tasks/arc064_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, x int
	fmt.Scan(&n, &x)
	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	res := 0
	for i := 0; i < n-1; i++ {
		t := (a[i] + a[i+1]) - x
		if t > 0 {
			res += t
			diff := t - a[i+1]
			if diff > 0 {
				a[i+1] = 0
				a[i] -= diff - a[i+1]
			} else {
				a[i+1] -= t
			}
		}
	}
	fmt.Println(res)
}
```