# C - H and V
[[bit全探索]] [[全探索]] [[Brown]] [[ABC]] [[Go]]
#bit全探索 #全探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc173/tasks/abc173_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var h, w, k int
	fmt.Scan(&h, &w, &k)

	c := make([]string, h)
	for i := range c {
		fmt.Scan(&c[i])
	}

	res := 0
	for bit := 0; bit < 1<<h; bit++ {
		for bit2 := 0; bit2 < 1<<w; bit2++ {
			cnt := 0
			for i := 0; i < h; i++ {
				for j := 0; j < w; j++ {
					if bit&(1<<i) == 0 && bit2&(1<<j) == 0 && c[i][j] == '#' {
						cnt++
					}
				}
			}
			if cnt == k {
				res++
			}
		}
	}

	fmt.Println(res)
}
```