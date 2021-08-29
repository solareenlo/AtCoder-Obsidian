# B - 錠
[[ABS]] [[min-max]] [[Gray]] [[ABC]] [[Go]]
#ABS #min-max #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc013/tasks/abc013_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scan(&a, &b)

	if a < b {
		a, b = b, a
	}

	if a-b > 5 {
		fmt.Println(10 - a + b)
	} else {
		fmt.Println(a - b)
	}
}
```