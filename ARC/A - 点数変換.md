# A - 点数変換
[[sort]] [[Green]] [[ARC]] [[Go]]
#sort #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc043/tasks/arc043_a

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
	var a, b float64
	fmt.Fscan(in, &n, &a, &b)

	s := make([]float64, n)
	x := 0.0
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &s[i])
		x += s[i]
	}
	sort.Float64s(s)

	if s[n-1] == s[0] {
		fmt.Println(-1)
	} else {
		p := b / (s[n-1] - s[0])
		fmt.Println(p, a-x*p/float64(n))
	}
}
```