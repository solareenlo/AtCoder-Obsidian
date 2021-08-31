# D - 高橋くんと木の直径
[[doble-sweep]] [[ACL]] [[Light Blue]] [[ABC]] [[Go]]
#double-sweep #ACL #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc019/tasks/abc019_4

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	var d, m, I int
	for i := 2; i <= n; i++ {
		fmt.Println("? 1", i)
		fmt.Scan(&d)
		if d > m {
			m, I = d, i
		}
	}

	m = 0
	for i := 1; i <= n; i++ {
		fmt.Println("?", I, i)
		fmt.Scan(&d)
		if d > m {
			m = d
		}
	}
	fmt.Println("!", m)
}
```