# A - Simple Calculator
[[min-max]] [[Brown]] [[AGC]] [[Go]]
#min-max #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc008/tasks/agc008_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x, y int
	fmt.Scan(&x, &y)

	tmp := 2
	if x < y {
		tmp = 0
	}
	fmt.Println(min(abs(x+y)+1, abs(x-y)+tmp))
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```