# D - Line++
[[無向グラフ]] [[2点間の最短距離]] [[Green]] [[ABC]] [[Go]]
#無向グラフ #2点間の最短距離 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc160/tasks/abc160_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, x, y int
	fmt.Scan(&n, &x, &y)
	x--
	y--

	res := make([]int, n)
	for i := 0; i < n; i++ {
		for j := i + 1; j < n; j++ {
			mini := min(min(abs(j-i), abs(x-i)+1+abs(j-y)), abs(y-i)+1+abs(j-x))
			mini--
			res[mini]++
		}
	}

	for i := 0; i < n-1; i++ {
		fmt.Println(res[i])
	}
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```