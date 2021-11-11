# C - A x B + C
[[組合せ]] [[Gray]] [[ABC]] [[Go]]
#組合せ #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc179/tasks/abc179_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res := 0
	for i := 1; i < n; i++ {
		res += (n - 1) / i
	}

	fmt.Println(res)
}
```