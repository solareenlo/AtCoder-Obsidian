# C - Same Integers
[[パターン]] [[Gray]] [[ABC]] [[Go]]
#パターン #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc093/tasks/arc094_a

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	num := make([]int, 3)
	for i := range num {
		fmt.Scan(&num[i])
	}
	sort.Ints(num)

	diff := num[2] - num[0] + num[2] - num[1]
	if diff%2 != 0 {
		fmt.Println(diff/2 + 2)
	} else {
		fmt.Println(diff / 2)
	}
}
```