# C - Not Equal
[[sort]] [[Gray]] [[ABC]] [[Go]]
#sort #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc209/tasks/abc209_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Scan(&n)

	c := make([]int, n)
	for i := range c {
		fmt.Fscan(in, &c[i])
	}
	sort.Ints(c)

	res := int64(1)
	for i := range c {
		res = res * int64(c[i]-i) % int64(1000000007)
	}
	fmt.Println(res)
}
```