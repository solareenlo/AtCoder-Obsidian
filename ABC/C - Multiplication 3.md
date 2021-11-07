# C - Multiplication 3
[[round]] [[Brown]] [[ABC]] [[Go]]
#round #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc169/tasks/abc169_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var a int
	var b float64
	fmt.Scan(&a, &b)

	fmt.Println((a * int(math.Round(b*100))) / 100)
}
```