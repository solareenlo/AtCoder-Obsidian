# D - アンバランス
[[文字列]] [[考察]] [[Light Blue]] [[ARC]] [[Go]]
#文字列 #考察 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc059/tasks/arc059_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	for i := 1; i < len(s); i++ {
		if s[i] == s[i-1] {
			fmt.Println(i, i+1)
			return
		}
	}

	for i := 2; i < len(s); i++ {
		if s[i] == s[i-2] {
			fmt.Println(i-1, i+1)
			return
		}
	}

	fmt.Println(-1, -1)
}
```