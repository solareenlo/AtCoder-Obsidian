# A - Digit Sum 2
[[桁]] [[Gray]] [[AGC]] [[Go]]
#桁 #Gray #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc021/tasks/agc021_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := 0
	for n = n + 1; n > 9; n /= 10 {
		a += 9
	}
	fmt.Println(a + n - 1)
}
```