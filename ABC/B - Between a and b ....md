# B - Between a and b ...
[[数学的考察]] [[Brown]] [[ABC]] [[Go]]
#数学的考察 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc048/tasks/abc048_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, x int
	fmt.Scan(&a, &b, &x)

	cntA := -1
	if a != 0 {
		cntA = (a - 1) / x
	}
	cntB := b / x
	fmt.Println(cntB - cntA)
}
```