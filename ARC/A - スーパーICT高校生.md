# A - スーパーICT高校生
[[文字列]] [[部分文字列]] [[Gray]] [[ARC]] [[Go]]
#文字列 #誘導部分グラフ #Gray #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc022/tasks/arc022_1

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var s string
	fmt.Scan(&s)

	s = strings.ToUpper(s)
	posI := max(strings.Index(s, "I"), 0)
	posC := max(strings.Index(s[posI:], "C"), 0)
	posC += posI
	posT := max(strings.Index(s[posC:], "T"), 0)
	posT += posC

	if posI < posC && posC < posT {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```