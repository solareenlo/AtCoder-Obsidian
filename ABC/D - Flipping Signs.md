# D - Flipping Signs
[[貪欲法]] [[Green]] [[ABC]] [[Go]]
#貪欲法 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc125/tasks/abc125_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	cnt, mini, sum := 0, 1<<60, 0
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		if a < 0 {
			cnt++
		}
		mini = min(mini, abs(a))
		sum += abs(a)
	}

	if cnt%2 != 0 {
		sum -= mini * 2
	}
	fmt.Println(sum)
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