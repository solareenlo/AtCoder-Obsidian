# B - 文字数カウント
[[カウント]] [[Gray]] [[ABC]] [[Go]]
#カウント #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc028/tasks/abc028_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	m := make([]int, 6)
	for i := range s {
		m[s[i]-'A']++
	}
	res := fmt.Sprint(m)
	fmt.Println(res[1 : len(res)-1])
}
```