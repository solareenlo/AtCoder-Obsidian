# B - Multiplication 2
[[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc169/tasks/abc169_b

## 解き方
### Code
```go
package main

import (
	"fmt"
)

func main() {
	var n int
	fmt.Scan(&n)

	res := 1
	for i := 0; i < n; i++ {
		var a int
		fmt.Scan(&a)
		if a == 0 {
			res = 0
		}
		if res != 0 && a > 1000000000000000000/res {
			res = -1
		}
		if res != -1 {
			res *= a
		}
	}

	fmt.Println(res)
}
```