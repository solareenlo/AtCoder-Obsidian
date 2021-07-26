# I - 和がNの区間
[[尺取法]] [[Black]] [[Others]] [[Go]]
#尺取法 #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/chokudai_S001/tasks/chokudai_S001_i

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	r, sum, res := 0, 0, 0
	for l := 0; l < n; l++ {
		for r < n && sum < n {
			sum += a[r]
			r++
		}
		if sum == n {
			res++
		}
		sum -= a[l]
	}
	fmt.Println(res)
}
```