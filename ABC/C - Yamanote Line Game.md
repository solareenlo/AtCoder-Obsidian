# C - Yamanote Line Game
[[シミュレーション]] [[Gray]] [[ABC]] [[Go]]
#シミュレーション #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc244/tasks/abc244_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	used := make([]bool, 2005)
	for {
		for i := 1; i <= 2*n+1; i++ {
			if !used[i] {
				fmt.Println(i)
				used[i] = true
				break
			}
		}
		var res int
		fmt.Scan(&res)
		if res == 0 {
			break
		}
		used[res] = true
	}
}
```