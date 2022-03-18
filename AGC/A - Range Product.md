# A - Range Product
[[if]] [[Gray]] [[AGC]] [[Go]]
#if #Gray #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc002/tasks/agc002_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scan(&a, &b)

	if a <= 0 && 0 <= b {
		fmt.Println("Zero")
	} else if a > 0 || (b-a)%2 == 1 {
		fmt.Println("Positive")
	} else {
		fmt.Println("Negative")
	}
}
```