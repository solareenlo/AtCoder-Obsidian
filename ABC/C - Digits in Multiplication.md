# C - Digits in Multiplication
[[桁]] [[min-max]] [[Brown]] [[ABC]] [[Go]]
#桁 #min-max #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc057/tasks/abc057_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var n int
	fmt.Scan(&n)

	res := cntDisits(n)
	for i := 1; i*i <= n; i++ {
		if n%i != 0 {
			continue
		}
		res = min(res, max(cntDisits(i), cntDisits(n/i)))
	}
	fmt.Println(res)
}

func cntDisits(n int) int {
	return len(strconv.Itoa(n))
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```