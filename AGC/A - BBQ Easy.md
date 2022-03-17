# A - BBQ Easy
[[sort]] [[Gray]] [[AGC]] [[Go]]
#sort #Gray #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc001/tasks/agc001_a

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

	a := make([]int, 2*n)
	for i := 0; i < n*2; i++ {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)

	s := 0
	for i := 0; i < 2*n; i += 2 {
		s += a[i]
	}
	fmt.Println(s)
}
```