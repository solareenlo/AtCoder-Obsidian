# B - Exactly N points
[[考察]] [[Green]] [[AGC-Like]] [[Go]]
#考察 #Green #AGC-Like #Go 

## 問題
- https://atcoder.jp/contests/cf16-final-open/tasks/codefestival_2016_final_b

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
	m := 0
	for m*(m+1)/2 < n {
		m++
	}
	k := m*(m+1)/2 - n
	for i := 1; i < k; i++ {
		fmt.Fprintln(out, i)
	}
	for i := k + 1; i <= m; i++ {
		fmt.Fprintln(out, i)
	}
}
```