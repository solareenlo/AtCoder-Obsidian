# D - Rectangles
[[全探索]] [[Brown]] [[ABC]] [[Go]]
#全探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc218/tasks/abc218_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	type pair struct{ x, y int }
	m := map[pair]bool{}
	for i := 0; i < n; i++ {
		var x, y int
		fmt.Scan(&x, &y)
		m[pair{x, y}] = true
	}

	cnt := 0
	for i := range m {
		for j := range m {
			if i.x < j.x && i.y < j.y {
				if m[pair{i.x, j.y}] && m[pair{j.x, i.y}] {
					cnt++
				}
			}
		}
	}
	fmt.Println(cnt)
}
```