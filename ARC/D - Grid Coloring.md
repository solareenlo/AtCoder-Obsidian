# D - Grid Coloring
[[グリッド]] [[Green]] [[ARC]] [[Go]]
#グリッド #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc080/tasks/arc080_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var h, w, n int
	fmt.Scan(&h, &w, &n)

	c := make([]int, 0)
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		for j := 0; j < a; j++ {
			c = append(c, i+1)
		}
	}

	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			k := j
			if i%2 != 0 {
				k = w - j - 1
			}
			fmt.Print(c[i*w+k], " ")
		}
		fmt.Println()
	}
}
```
