# B - Find Symmetries
[[グリッド]] [[Light Blue]] [[AGC]] [[Go]]
#グリッド #Light_Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc023/tasks/agc023_b

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

	c := make([]string, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &c[i])
	}

	ans := 0
	for k := 0; k < n; k++ {
		flag := true
		for i := 0; i < n; i++ {
			for j := 0; j < n; j++ {
				if c[i][j] != c[(j+k)%n][(i+n-k)%n] {
					flag = false
				}
			}
		}
		if flag {
			ans += n
		}
	}
	fmt.Println(ans)
}
```