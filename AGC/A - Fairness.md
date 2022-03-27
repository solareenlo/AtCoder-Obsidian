# A - Fairness
[[考察]] [[Gray]] [[AGC]] [[Go]]
#考察 #Gray #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc024/tasks/agc024_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b, c, k int
	fmt.Scan(&a, &b, &c, &k)

	fmt.Println((k%2*2 - 1) * (b - a))
}```