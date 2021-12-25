# D - Harlequin
[[数学的考察]] [[メモ化再帰]] [[Green]] [[ABC-Like]] [[Go]]
#数学的考察 #メモ化再帰 #Green #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/caddi2018b/tasks/caddi2018_b

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

	cnt := 0
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		if a%2 != 0 {
			cnt++
		}
	}
	if cnt != 0 {
		fmt.Println("first")
	} else {
		fmt.Println("second")
	}
}
```