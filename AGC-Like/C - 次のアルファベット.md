# C - 次のアルファベット
[[文字列]] [[辞書順]] [[Green]] [[AGC-Like]] [[Go]]
#文字列 #辞書順 #Green #AGC-Like #Go 

## 問題
- https://atcoder.jp/contests/code-festival-2016-quala/tasks/codefestival_2016_qualA_c

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

	var S string
	var k int
	fmt.Fscan(in, &S, &k)
	s := strings.Split(S, "")

	for i := 0; i < len(s); i++ {
		tmp := (int('z'-s[i][0]) + 1) % 26
		if k >= tmp {
			k -= tmp
			s[i] = "a"
		}
	}

	k %= 26
	s[len(s)-1] = string(s[len(s)-1][0] + byte(k))
	fmt.Println(strings.Join(s, ""))
}
```