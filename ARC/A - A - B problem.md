# A - A - B problem
[[桁]] [[Brown]] [[ARC]] [[Go]]
#桁 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc039/tasks/arc039_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scan(&a, &b)

	var c, d int
	if a/10 == 99 && b/10 == 10 {
		c = 999
		d = 100
	} else if a/100 == 9 && b/100 == 1 {
		c = a%10 + 990
		d = b%10 + 100
	} else {
		c = a%100 + 900
		d = b%100 + 100
	}

	fmt.Println(max(c-b, a-d))
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```