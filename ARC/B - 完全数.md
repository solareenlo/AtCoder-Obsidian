# B - 完全数
[[約数]] [[Green]] [[ARC]] [[Go]]
#約数 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc026/tasks/arc026_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	div := divList(n)
	sum := 0
	for k, _ := range div {
		sum += k
	}
	sum -= n

	if sum == n {
		fmt.Println("Perfect")
	} else if sum > n {
		fmt.Println("Abundant")
	} else {
		fmt.Println("Deficient")
	}
}

func divList(n int) map[int]struct{} {
	div := map[int]struct{}{}
	for i := 1; i*i <= n; i++ {
		if n%i == 0 {
			div[i] = struct{}{}
			if i*i != n {
				div[n/i] = struct{}{}
			}
		}
	}
	return div
}
```