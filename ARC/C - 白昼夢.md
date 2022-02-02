# C - 白昼夢
[[Regex]] [[Green]] [[ARC]] [[Go]]
#Regex #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc065/tasks/arc065_a

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