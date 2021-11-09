# F - Intervals on Tree
[[Graph]] [[Union-Find]] [[Blue]] [[ABC]] [[Go]]
#Graph #Union-Find #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc173/tasks/abc173_f

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

	res := n * (n + 1) * (n + 2) / 6
	for i := 0; i < n-1; i++ {
		var u, v int
		fmt.Fscan(in, &u, &v)
		if u > v {
			u, v = v, u
		}
		res -= u * (n - v + 1)
	}
	fmt.Println(res)
}
```