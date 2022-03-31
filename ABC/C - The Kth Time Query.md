# C - The Kth Time Query
[[数列]] [[map]] [[Gray]] [[ABC]] [[Go]]
#数列 #map #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc235/tasks/abc235_c

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

	var n, q int
	fmt.Fscan(in, &n, &q)

	m := make(map[int][]int)
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		m[a] = append(m[a], i+1)
	}

	for i := 0; i < q; i++ {
		var x, k int
		fmt.Fscan(in, &x, &k)
		if len(m[x]) < k {
			fmt.Println(-1)
		} else {
			fmt.Println(m[x][k-1])
		}
	}
}
```