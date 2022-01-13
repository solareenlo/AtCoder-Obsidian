# B - 細長いお菓子
[[尺取法]] [[Light Blue]] [[ARC]] [[Go]]
#尺取法 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc022/tasks/arc022_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	pre, res := 0, 1
	m := map[int]int{}
	for i := 1; i < n+1; i++ {
		var a int
		fmt.Scan(&a)
		pre = max(pre, m[a])
		res = max(res, i-pre)
		m[a] = i
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```