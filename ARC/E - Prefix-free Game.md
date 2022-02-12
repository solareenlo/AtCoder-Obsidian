# E - Prefix-free Game
[[文字列]] [[完全二分木]] [[Grundy数]] [[xor]] [[Orange]] [[ARC]] [[Go]]
#文字列 #完全二分木 #Grundy数 #xor #Orange #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc087/tasks/arc087_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var t = [1000010][2]int{}

func f(x, d int) int {
	if x != 0 {
		return f(t[x][0], d-1) ^ f(t[x][1], d-1)
	}
	return d & -d
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, l int
	fmt.Fscan(in, &n, &l)

	b := 1
	for j := 0; j < n; j++ {
		var s string
		fmt.Fscan(in, &s)
		p := 1
		for i := 0; i < len(s); i++ {
			if t[p][s[i]^48] == 0 {
				b++
				t[p][s[i]^48] = b
			}
			p = t[p][s[i]^48]
		}
	}

	if f(1, l+1) != 0 {
		fmt.Println("Alice")
	} else {
		fmt.Println("Bob")
	}
}
```