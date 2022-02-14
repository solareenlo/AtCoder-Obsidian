# F - Strange Nim
[[Grundy数]] [[Yellow]] [[ARC]] [[Go]]
#Grundy数 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc091/tasks/arc091_d

## 解き方
### Code
```Go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var t int
	fmt.Fscan(in, &t)

	k := 0
	for i := 0; i < t; i++ {
		var a, b int
		fmt.Fscan(in, &a, &b)
		for a%b != 0 {
			a -= (a%b + a/b) / (a/b + 1) * (a/b + 1)
		}
		k ^= (a / b)
	}

	if k != 0 {
		fmt.Println("Takahashi")
	} else {
		fmt.Println("Aoki")
	}
}
```