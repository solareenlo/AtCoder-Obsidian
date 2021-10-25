# F - Distinct Numbers
[[数列]] [[狭義単調増加数列]] [[累積和]] [[Yellow]] [[ABC]] [[Go]]
#数列 #狭義単調増加数列 #累積和 #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc143/tasks/abc143_f

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

	cnt := make([]int, n)
	sum := make([]int, n)
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		sum[cnt[a-1]]++
		cnt[a-1]++
	}

	itr, acc := n, n
	for i := 1; i < n+1; i++ {
		for acc < itr*i {
			itr--
			acc -= sum[itr]
		}
		fmt.Fprintln(out, itr)
	}
}
```