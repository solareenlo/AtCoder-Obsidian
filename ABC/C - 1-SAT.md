# C - 1-SAT
[[map]] [[部分文]] [[Gray]] [[ABC]] [[Go]]
#map #文字列 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc187/tasks/abc187_c

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
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	fmt.Fscan(in, &n)
	m := make(map[string]int)

	for i := 0; i < n; i++ {
		var s string
		fmt.Fscan(in, &s)
		m[s]++
	}

	for k, _ := range m {
		if m["!"+k] != 0 {
			fmt.Fprintln(out, k)
			return
		}
	}

	fmt.Println("satisfiable")
}
```