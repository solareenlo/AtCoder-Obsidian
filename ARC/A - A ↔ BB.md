# A - A ↔ BB
[[Regex]] [[Gray]] [[ARC]] [[Go]]
#Regex #Gray #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc136/tasks/arc136_a

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	var s string
	fmt.Fscan(in, &n, &s)

	s = strings.ReplaceAll(s, "A", "BB")
	s = strings.ReplaceAll(s, "BB", "A")
	fmt.Fprintln(out, s)
}
```