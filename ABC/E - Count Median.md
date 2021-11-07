# E - Count Median
[[中央値]] [[数学的考察]] [[Light Blue]] [[ABC]] [[Go]]
#中央値 #数学的考察 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc169/tasks/abc169_e

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
	b := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i], &b[i])
	}
	sort.Ints(a)
	sort.Ints(b)

	var l, r int
	if n%2 != 0 {
		l = a[n/2]
		r = b[n/2]
	} else {
		l = a[n/2-1] + a[n/2]
		r = b[n/2-1] + b[n/2]
	}

	fmt.Println(r - l + 1)
}
```