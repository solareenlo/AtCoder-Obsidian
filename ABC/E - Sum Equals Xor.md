# E - Sum Equals Xor
[[xor]] [[数学的考察]] [[Light Blue]] [[ABC]] [[Go]]
#xor #数学的考察 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc129/tasks/abc129_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var l string
	fmt.Scan(&l)

	mod := int(1e9 + 7)
	a, b := 0, 1
	for _, c := range l {
		a = (a * 3) % mod
		if c == '1' {
			a = (a + b) % mod
			b = (b * 2) % mod
		}
	}
	fmt.Println((a + b) % mod)
}
```