# A - LR Constraints
[[条件分岐]] [[Brown]] [[ARC]] [[Go]]
#条件分岐 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc124/tasks/arc124_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, K int
	fmt.Scan(&n, &K)
	a := make([]int, n)
	b := make([]bool, n)
	for i := 0; i < K; i++ {
		var c string
		var k int
		fmt.Scan(&c, &k)
		k--
		b[k] = true
		for j := 0; j < n; j++ {
			if (c == "L" && k <= j) || (c == "R" && j <= k) {
				a[j]++
			}
		}
	}
	res := 1
	for i := 0; i < n; i++ {
		if b[i] == false {
			res = res * a[i] % 998244353
		}
	}
	fmt.Println(res)
}
```