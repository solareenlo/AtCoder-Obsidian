# D - 高橋君と見えざる手
[[map]] [[min-max]] [[Green]] [[ABC]] [[Go]]
#map #min-max #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc047/tasks/arc063_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, t, a int
	fmt.Scan(&n, &t)

	mini, maxi := int(1e12), 0
	m := make(map[int]int)
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		m[a-mini]++
		maxi = max(maxi, a-mini)
		mini = min(mini, a)
	}
	fmt.Println(m[maxi])
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```