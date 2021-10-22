# C - Green Bin
[[文字列]] [[sort]] [[Brown]] [[ABC]] [[Go]]
#文字列 #sort #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc137/tasks/abc137_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)

	str := map[string]int{}
	res := 0
	for i := 0; i < n; i++ {
		var s string
		fmt.Scan(&s)
		b := make([]byte, len(s))
		for i := range s {
			b[i] = s[i]
		}
		sort.Slice(b, func(i, j int) bool {
			return b[i] < b[j]
		})
		res += str[string(b)]
		str[string(b)]++
	}
	fmt.Println(res)
}
```