# C - One Quadrillion and One Dalmatians
[[再帰関数]] [[Reverse]] [[Brown]] [[ABC]] [[Go]]
#再帰関数 #Reverse #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc171/tasks/abc171_c

## 解き方
### Code
```go
package main

import "fmt"

var s string

func main() {
	var n int
	fmt.Scan(&n)
	n--

	rec(n)
	fmt.Println(reverseString(s))
}

func reverseString(s string) string {
	res := []rune(s)
	for i, j := 0, len(res)-1; i < j; i, j = i+1, j-1 {
		res[i], res[j] = res[j], res[i]
	}
	return string(res)
}

func rec(n int) {
	if n/26 == 0 {
		c := 'a' + (n % 26)
		s += string(c)
		return
	}
	rec(n % 26)
	rec(n/26 - 1)
}
```