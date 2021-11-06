# D - Floor Function
[[floor]] [[広義短調増加]] [[Brown]] [[ABC]] [[Go]]
#floor #広義短調増加 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc165/tasks/abc165_d

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var a, b, n int
	fmt.Scan(&a, &b, &n)

	var x int
	if n < b-1 {
		x = n
	} else {
		x = b - 1
	}

	fmt.Println(math.Floor(float64(a * (x % b) / b)))
}
```