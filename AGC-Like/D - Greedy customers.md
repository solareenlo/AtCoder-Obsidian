# D - Greedy customers
[[シミュレーション]] [[Blue]] [[AGC-Like]] [[Go]]
#シミュレーション #Blue #AGC-Like #Go 

## 問題
- https://atcoder.jp/contests/code-festival-2016-qualb/tasks/codefestival_2016_qualB_d

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

	ans := 0
	for i, v := 1, 0; i <= n; i++ {
		var a int
		fmt.Fscan(in, &a)
		if a > v+1 {
			ans += (a - 1) / (v + 1)
		}
		if a == v+1 {
			v++
		}
		if v == 0 {
			v = 1
		}
	}
	fmt.Println(ans)
}
```