# C - Multiple of 7
[[文字列]] [[貪欲法]] [[Blue]] [[ARC]] [[Go]]
#文字列 #貪欲法 #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc129/tasks/arc129_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"math"
	"os"
)

func main() {
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	fmt.Scan(&n)

	mo := 1
	jg := false
	for n > 0 {
		k := int(math.Floor(math.Sqrt(2.0*float64(n)+1.0/4.0) - 1/2.0))
		if jg {
			fmt.Fprint(out, mo)
			mo *= 10
			mo %= 7
		}
		for i := 0; i < k; i++ {
			fmt.Fprint(out, 7)
			mo *= 10
			mo %= 7
		}
		jg = true
		n -= (k*k + k) / 2
	}
}
```