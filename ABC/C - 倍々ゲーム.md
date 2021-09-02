# C - 倍々ゲーム
[[二分木]] [[探索]] [[Green]] [[ABC]] [[Go]]
#二分木 #探索 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc027/tasks/abc027_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var N int
	fmt.Scan(&N)

	depth := 1
	for n := N + 1; n > 1; {
		n = (n + depth%2) / 2
		depth++
	}
	if depth%2 == 1 {
		fmt.Println("Takahashi")
	} else {
		fmt.Println("Aoki")
	}
}
```