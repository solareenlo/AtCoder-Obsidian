# E - This Message Will Self-Destruct in 5s
[[全探索]] [[探索]] [[数学的考察]] [[Green]] [[ABC]] [[Go]]
#全探索 #探索 #数学的考察 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc166/tasks/abc166_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	p := make([]int, n+1)
	res := 0
	for i := 0; i < n; i++ {
		var a int
		fmt.Scan(&a)
		if i+a < n {
			p[i+a]++
		}
		if i-a >= 0 {
			res += p[i-a]
		}
	}

	fmt.Println(res)
}
```