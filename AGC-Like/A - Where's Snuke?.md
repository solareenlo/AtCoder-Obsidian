# A - Where's Snuke?
[[シミュレーション]] [[Gray]] [[AGC-Like]] [[Go]]
#シミュレーション #Gray #AGC-Like #Go 

## 問題
- https://atcoder.jp/contests/cf16-final-open/tasks/codefestival_2016_final_a

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

	var h, w int
	fmt.Fscan(in, &h, &w)

	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			var s string
			fmt.Fscan(in, &s)
			if s == "snuke" {
				fmt.Fprint(out, string('A'+j), i+1, "\n")
			}
		}
	}
}
```