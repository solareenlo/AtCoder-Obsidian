# B - こだわりの名前
[[文字列]] [[回文]] [[Light Blue]] [[ARC]] [[Go]]
#文字列 #回文 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc019/tasks/arc019_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	cnt := 0
	for i := 0; i < n/2; i++ {
		if s[i] != s[n-1-i] {
			cnt++
		}
	}

	res := 25 * n
	if cnt == 1 {
		res -= 2
	}
	if cnt == 0 && n%2 != 0 {
		res -= 25
	}

	fmt.Println(res)
}
```