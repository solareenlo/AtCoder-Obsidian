# C - Buy an Integer
[[二分探索]] [[Brown]] [[ABC]] [[Go]]
#二分探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc146/tasks/abc146_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var a, b, x int
	fmt.Scan(&a, &b, &x)

	l, r := 0, 1000000001
	for r-l > 1 {
		mid := (l + r) / 2
		tmp := a*mid + b*len(strconv.Itoa(mid))
		if tmp <= x {
			l = mid
		} else {
			r = mid
		}
	}

	fmt.Println(l)
}
```