# D - Remainder Reminder
[[全探索]] [[探索]] [[Green]] [[ARC]] [[Go]]
#全探索 #探索 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc091/tasks/arc091_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	cnt := 0
	if k == 0 {
		cnt = n * n
	} else {
		for b := k + 1; b <= n; b++ {
			div := n / b
			rem := n % b
			cnt += div*max(0, b-k) + max(0, rem-k+1)
		}
	}
	fmt.Println(cnt)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
