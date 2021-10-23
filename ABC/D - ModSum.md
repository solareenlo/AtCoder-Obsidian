# D - ModSum
[[数列]] [[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#数列 #数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc139/tasks/abc139_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	fmt.Println(n * (n - 1) / 2)
}
```