# D - Moves on Binary Tree
[[2進数]] [[完全二分木]] [[Brown]] [[ABC]] [[Go]]
#2進数 #完全二分木 #Brow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc243/tasks/abc243_d

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

	var n, x int
	var s string
	fmt.Fscan(in, &n, &x, &s)

	const maxn = 1000000000000000000
	cnt := 0
	for i := 0; i < n; i++ {
		if s[i] == 'U' {
			if cnt != 0 {
				cnt--
			} else {
				x /= 2
			}
		} else {
			if x*2 > maxn {
				cnt++
			} else {
				if s[i] == 'L' {
					x *= 2
				} else {
					x = x*2 + 1
				}
			}
		}
	}
	fmt.Println(x)
}
```