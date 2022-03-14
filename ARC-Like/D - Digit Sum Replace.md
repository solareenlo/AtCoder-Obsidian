# D - Digit Sum Replace
[[桁]] [[Blue]] [[ARC-Like]] [[Go]]
#桁 #Blue #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/ddcc2020-qual/tasks/ddcc2020_qual_d

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

	var m int
	fmt.Fscan(in, &m)

	sum := 0
	ans := 0
	for i := 0; i < m; i++ {
		var a, b int
		fmt.Fscan(in, &a, &b)
		sum += a * b
		ans += b
	}

	sum--
	ans--
	fmt.Println(sum/9 + ans)
}
```