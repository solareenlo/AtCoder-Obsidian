# C - Modulo Summation
[[MOD]] [[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#MOD #数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc103/tasks/abc103_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, sum int
	fmt.Scan(&n)
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		sum += a - 1
	}
	fmt.Println(sum)
}
```