# D - ロボット
[[sort]] [[Light Blue]] [[ABC]] [[Go]]
#sort #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc027/tasks/abc027_d

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var s string
	fmt.Scan(&s)

	plus, minus := 0, 0
	a := make([]int, 0)
	for i := len(s) - 1; i >= 0; i-- {
		switch s[i] {
		case 'M':
			a = append(a, plus-minus)
		case '+':
			plus++
		case '-':
			minus++
		}
	}
	sort.Ints(a)

	n := len(a)
	res := 0
	for i := 0; i < n; i++ {
		if i < n/2 {
			res -= a[i]
		} else {
			res += a[i]
		}
	}
	fmt.Println(res)
}
```