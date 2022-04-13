# B - Count 1's
[[数列]] [[flip]] [[Green]] [[ARC]] [[Go]]
#数列 #flip #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc137/tasks/arc137_b

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

	now := 0
	l, r := 0, 0
	al, ar := 0, 0
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		if a != 0 {
			now++
		} else {
			now--
		}
		if r < now {
			r++
		}
		if l > now {
			l--
		}
		if ar < now-l {
			ar++
		}
		if al > now-r {
			al--
		}
	}
	fmt.Println(ar - al + 1)
}
```