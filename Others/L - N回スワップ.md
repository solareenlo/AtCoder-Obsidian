# L - N回スワップ
[[swap]] [[Black]] [[Others]] [[Go]]
#swap #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/chokudai_S001/tasks/chokudai_S001_l

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
	fmt.Scan(&n)

	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
		a[i]--
	}

	res := 0
	for i := 0; i < n; i++ {
		for i != a[i] {
			a[a[i]], a[i] = a[i], a[a[i]]
			res++
		}
	}
	if (n-res)&1 == 0 {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```