# C - Kaprekar Number
[[文字列]] [[Reverse]] [[Gray]] [[ABC]] [[Go]]
#文字列 #Reverse #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc192/tasks/abc192_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
	"strconv"
	"strings"
)

func main() {
	var n string
	var k int
	fmt.Scan(&n, &k)

	for i := 0; i < k; i++ {
		slice := strings.Split(n, "")
		sort.Strings(slice)
		s, _ := strconv.Atoi(strings.Join(slice, ""))
		sort.Sort(sort.Reverse(sort.StringSlice(slice)))
		t, _ := strconv.Atoi(strings.Join(slice, ""))
		n = strconv.Itoa(t - s)
	}
	fmt.Println(n)
}
```