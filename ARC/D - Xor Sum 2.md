# D - Xor Sum 2
[[xor]] [[累積和]] [[二分探索]] [[Light Blue]] [[ARC]] [[Go]]
#xor #累積和 #二分探索 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc098/tasks/arc098_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	var a int
	sum := make([]int, n)
	xor := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		sum[i] = a
		xor[i] = a
	}

	for i := 1; i < n; i++ {
		xor[i] ^= xor[i-1]
		sum[i] += sum[i-1]
	}

	res := 0
	for i := 0; i < n; i++ {
		l, r := i, n
		for r-l > 1 {
			m := (l + r) / 2
			x := xor[m]
			if i != 0 {
				x ^= xor[i-1]
			}
			s := sum[m]
			if i != 0 {
				s -= sum[i-1]
			}
			if x == s {
				l = m
			} else {
				r = m
			}
		}
		res += l - i + 1
	}
	fmt.Println(res)
}
```
