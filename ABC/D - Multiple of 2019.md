# D - Multiple of 2019
[[文字列]] [[Light Blue]] [[ABC]] [[Go]]
#文字列 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc164/tasks/abc164_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	cnt := [2019]int{}
	cnt[0] = 1
	now, res, p := 0, 0, 1
	for i := n - 1; i >= 0; i-- {
		now = (now + int(s[i]-'0')*p) % 2019
		res += cnt[now]
		cnt[now]++
		p = p * 10 % 2019
	}

	fmt.Println(res)
}
```