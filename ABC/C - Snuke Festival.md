# C - Snuke Festival
[[二分探索]] [[lower_bound]] [[upper_bound]] [[Green]] [[ABC]] [[Go]]
#二分探索 #lower_bound #upper_bound #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc077/tasks/arc084_a

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
	a, b, c := make([]int, n), make([]int, n), make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)
	for i := range b {
		fmt.Fscan(in, &b[i])
	}
	for i := range c {
		fmt.Fscan(in, &c[i])
	}
	sort.Ints(c)

	res := 0
	for i := 0; i < n; i++ {
		cntA := sort.SearchInts(a, b[i])
		cntC := n - sort.SearchInts(c, b[i]+1)
		res += cntA * cntC
	}
	fmt.Println(res)
}
```