# E - Divisible Substring
[[文字列]] [[部分文字列]] [[全探索]] [[Blue]] [[ABC]] [[Go]]
#文字列 #部分文字列 #全探索 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc158/tasks/abc158_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, p int
	var s string
	fmt.Scan(&n, &p, &s)

	cnt := [10010]int{}
	now, t := 0, 1
	res := 0
	if p == 2 || p == 5 {
		for i := 0; i < n; i++ {
			if int(s[i]-'0')%p == 0 {
				res += i + 1
			}
		}
	} else {
		cnt[0] = 1
		for i := n - 1; i >= 0; i-- {
			now += int(s[i]-'0') * t
			now %= p
			res += cnt[now]
			cnt[now]++
			t = t * 10 % p
		}
	}

	fmt.Println(res)
}
```