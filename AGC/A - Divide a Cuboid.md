# A - Divide a Cuboid
[[立体]] [[Brown]] [[AGC]] [[Go]]
#立体 #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc004/tasks/agc004_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, c int
	fmt.Scan(&a, &b, &c)

	if a%2 == 0 || b%2 == 0 || c%2 == 0 {
		fmt.Println(0)
	} else {
		fmt.Println(min(a*b, b*c, c*a))
	}
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