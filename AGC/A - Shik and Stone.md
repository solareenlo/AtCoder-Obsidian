# A - Shik and Stone
[[文字列]] [[Brown]] [[AGC]] [[Go]]
#文字列 #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc007/tasks/agc007_a

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

	var h, w int
	fmt.Fscan(in, &h, &w)

	ans := 0
	for i := 0; i < h; i++ {
		var a string
		fmt.Fscan(in, &a)
		for j := range a {
			if a[j] == '#' {
				ans++
			}
		}
	}
	if ans == h+w-1 {
		fmt.Println("Possible")
	} else {
		fmt.Println("Impossible")
	}
}
```