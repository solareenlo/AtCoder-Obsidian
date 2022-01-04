# B - 迷子のCDケース
[[全探索]] [[Brown]] [[ARC]] [[Go]]
#全探索 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc007/tasks/arc007_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	cd := make([]int, n)
	for i := 0; i < n; i++ {
		cd[i] = i + 1
	}

	player := 0
	for i := 0; i < m; i++ {
		var disk int
		fmt.Scan(&disk)
		for j := 0; j < n; j++ {
			if cd[j] == disk {
				cd[j] = player
				player = disk
				break
			}
		}
	}

	for i := 0; i < n; i++ {
		fmt.Println(cd[i])
	}
}
```