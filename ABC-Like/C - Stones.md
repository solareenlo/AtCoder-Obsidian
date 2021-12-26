# C - Stones
[[グリッド]] [[min-max]] [[Green]] [[ABC-Like]] [[Go]]
#グリッド #min-max #Green #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/tenka1-2019-beginner/tasks/tenka1_2019_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	var s string
	fmt.Fscan(in, &n, &s)

	mini := n
	cntB := 0
	cntW := 0
	for i := 0; i < n; i++ {
		if s[i] == '.' {
			cntW++
		}
	}
	mini = min(mini, cntB+cntW)
	for i := 0; i < n; i++ {
		if s[i] == '#' {
			cntB++
		} else {
			cntW--
		}
		mini = min(mini, cntB+cntW)
	}

	fmt.Println(mini)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```