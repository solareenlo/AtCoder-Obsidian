# A - 経過日数
[[日付]] [[Gray]] [[ARC]] [[Go]]
#日付 #Gray #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc023/tasks/arc023_1

## 解き方
### Code
```go
package main

import "fmt"

func calDay(y, m, d int) int {
	res := 365*y + y/4 - y/100 + y/400 + (306*(m+1))/10 + d - 429
	return res
}

func main() {
	var y, m, d int
	fmt.Scan(&y, &m, &d)

	if m == 1 {
		y--
		m = 13
	}
	if m == 2 {
		y--
		m = 14
	}

	a := calDay(2014, 5, 17)
	b := calDay(y, m, d)

	fmt.Println(a - b)
}
```