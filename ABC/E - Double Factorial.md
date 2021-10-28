# E - Double Factorial
[[数学的考察]] [[Green]] [[ABC]] [[Go]]
#数学的考察 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc148/tasks/abc148_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res := 0
	if n%2 == 0 {
		tmp := 10
		for tmp <= n {
			res += n / tmp
			tmp *= 5
		}
	}

	fmt.Println(res)
}
```