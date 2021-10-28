# D - Brick Break
[[貪欲法]] [[Gray]] [[ABC]] [[Go]]
#貪欲法 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc148/tasks/abc148_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	num, cnt := 1, 0
	for i := 0; i < n; i++ {
		var tmp int
		fmt.Scan(&tmp)
		if num == tmp {
			num++
			cnt++
		}
	}

	if cnt == 0 {
		fmt.Println(-1)
	} else {
		fmt.Println(n - cnt)
	}
}
```