# B - Abbreviate Fox
[[文字列]] [[部分文字列]] [[Brown]] [[ARC]] [[Go]]
#文字列 #部分文字列 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc108/tasks/arc108_b

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

	t := make([]byte, 0)
	for i := range s {
		t = append(t, s[i])
		if len(t) >= 3 && t[len(t)-3] == 'f' && t[len(t)-2] == 'o' && t[len(t)-1] == 'x' {
			t = t[:len(t)-3]
		}
	}
	fmt.Println(len(t))
}
```