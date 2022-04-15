# B - 仲良しうさぎ
[[全探索]] [[Brown]] [[AGC-Like]] [[Go]]
#全探索 #Brown #AGC-Like #Go 

## 問題
- https://atcoder.jp/contests/code-festival-2016-quala/tasks/codefestival_2016_qualA_b

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

	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}

	cnt := 0
	for i := 1; i <= n; i++ {
		if a[a[i]] == i {
			cnt++
		}
	}
	fmt.Println(cnt / 2)
}
```