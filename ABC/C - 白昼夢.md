# C - 白昼夢
[[Regex]] [[Brown]] [[ABC]] [[Go]]
#Regex #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc049/tasks/arc065_a

## 解き方
### Code
```go
package main

import (
	"fmt"
	"regexp"
)

func main() {
	var s string
	fmt.Scan(&s)

	reg := regexp.MustCompile(`^(dream|dreamer|erase|eraser)*$`)
	if reg.MatchString(s) {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```