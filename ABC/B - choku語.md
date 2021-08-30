# B - choku語
[[文字列操作]] [[Replace]] [[Brown]] [[ABC]] [[Go]]
#文字列操作 #Replace #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc017/tasks/abc017_2

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var x string
	fmt.Scan(&x)

	res := "NO"
	s := [4]string{"ch", "o", "k", "u"}
	for i := range s {
		x = strings.Replace(x, s[i], "", -1)
	}

	if len(x) == 0 {
		res = "YES"
	}

	fmt.Println(res)
}
```