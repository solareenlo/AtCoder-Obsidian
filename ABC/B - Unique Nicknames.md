# B - Unique Nicknames
[[map]] [[Gray]] [[ABC]] [[Go]]
#map #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc247/tasks/abc247_b

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
	fmt.Fscan(in, &n)

	p := make(map[string]int)
	for i := 0; i < n; i++ {
		var s, t string
		fmt.Fscan(in, &s, &t)
		if p[t] != 0 {
			fmt.Println("No")
			return
		}
		p[s]++
		p[t]++
	}

	fmt.Println("Yes")
}
```