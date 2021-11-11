# E - Dist Max
[[マンハッタン距離]] [[数学的考察]] [[Green]] [[ABC]] [[Go]]
#マンハッタン距離 #数学的考察 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc178/tasks/abc178_e

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
	fmt.Fscan(in, &n)

	a := make([]int, n)
	s := make([]int, n)
	for i := 0; i < n; i++ {
		var x, y int
		fmt.Fscan(in, &x, &y)
		a[i] = x + y
		s[i] = x - y
	}
	sort.Ints(a)
	sort.Ints(s)

	fmt.Println(max(a[n-1]-a[0], s[n-1]-s[0]))
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```