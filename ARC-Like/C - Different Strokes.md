# C - Different Strokes
[[総和]] [[Green]] [[ARC-Like]] [[Go]]
#総和 #Green #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/nikkei2019-qual/tasks/nikkei2019_qual_c

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

	ans := 0
	c := make([]int, n+1)
	for i := 1; i <= n; i++ {
		var a, b int
		fmt.Fscan(in, &a, &b)
		c[i] = a + b
		ans -= b
	}
	tmp := c[1:]
	sort.Ints(tmp)

	for i := n; i > 0; i -= 2 {
		ans += c[i]
	}
	fmt.Println(ans)
}
```