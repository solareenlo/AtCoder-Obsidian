# C - X drawing
[[グリッド]] [[シミュレーション]] [[Brown]] [[ABC]] [[Go]]
#グリッド #シミュレーション #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc230/tasks/abc230_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b, p, q, r, s int
	fmt.Scan(&n, &a, &b, &p, &q, &r, &s)

	for i := p; i < q+1; i++ {
		for j := r; j < s+1; j++ {
			if i-j == a-b || i+j == a+b {
				fmt.Print("#")
			} else {
				fmt.Print(".")
			}
		}
		fmt.Println()
	}
}
```