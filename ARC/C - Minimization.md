# C - Minimization
[[数列]] [[Brown]] [[ARC]] [[Go]]
#数列 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc099/tasks/arc099_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)
	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	if n == k {
		fmt.Println(1)
	} else {
		diff := n - k
		div := diff / (k - 1)
		rem := diff % (k - 1)
		if rem != 0 {
			fmt.Println(1 + div + 1)
		} else {
			fmt.Println(1 + div)
		}
	}
}
```
