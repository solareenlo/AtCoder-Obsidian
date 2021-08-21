# D - 感雨時刻の整理
[[いもす法]] [[Light Blue]] [[ABC]] [[Go]]
#いもす法 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc001/tasks/abc001_4

## 解き方
### Code いもす法
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	t := make([]int, 1000)
	var tmp string
	var s, e int
	for i := n; i > 0; i-- {
		fmt.Scan(&tmp)
		fmt.Sscanf(tmp, "%04d-%04d", &s, &e)
		e = (e + 4) / 5
		t[s/5]++
		if e%20 == 12 {
			t[e+8]--
		} else {
			t[e]--
		}
	}
	for i, u, p := 0, 0, 0; i <= 480; i++ {
		u += t[i]
		if (u == 0 && p != 0) || (u != 0 && p == 0) {
			fmt.Printf("%04d", i*5)
			if p != 0 {
				fmt.Print("\n")
			} else {
				fmt.Print("-")
			}
		}
		p = u
	}
}
```