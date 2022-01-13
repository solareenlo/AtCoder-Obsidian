# B - Your Numbers are XORed...
[[xor]] [[Light Blue]] [[ARC]] [[Go]]
#xor #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc021/tasks/arc021_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	b := make([]int, n)
	x := 0
	for i := range b {
		fmt.Scan(&b[i])
		x ^= b[i]
	}

	if x != 0 {
		fmt.Println(-1)
		return
	}

	res := 0
	for i := 0; i < n; i++ {
		fmt.Println(res)
		res ^= b[i]
	}
}
```