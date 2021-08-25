# D - 禁止された数字
[[桁DP]] [[Blue]] [[ABC]] [[Go]]
#桁DP #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc007/tasks/abc007_4

## 解き方
### Code 桁DP
```go
package main

import (
	"fmt"
	"strconv"
)

func f(n int64) int64 {
	s := strconv.FormatInt(n, 10)
	dp0, dp1 := int64(0), int64(1)
	for i := 0; i < len(s); i++ {
		a := byte(0)
		if s[i] > '4' {
			a = 1
		}
		dp0 = dp0*8 + dp1*int64(s[i]-'0'-a)
		if s[i] != '4' && s[i] != '9' {
			dp1 &= 1
		} else {
			dp1 &= 0
		}
	}
	return n + 1 - (dp0 + dp1)
}

func main() {
	var a, b int64
	fmt.Scan(&a, &b)
	fmt.Println(f(b) - f(a-1))
}
```

### Code
```go
package main

import "fmt"

func f(n int64) int64 {
	m, b := int64(0), int64(1)
	for i := n; i > 0; i /= 10 {
		d := i % 10
		if d == 4 || d == 9 {
			m = 0
		}
		if d > 4 {
			m += (d - 1) * b
		} else {
			m += d * b
		}
		b *= 8
	}
	return n - m
}

func main() {
	var a, b int64
	fmt.Scan(&a, &b)
	fmt.Println(f(b+1) - f(a))
}
```