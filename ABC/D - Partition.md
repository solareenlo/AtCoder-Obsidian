# D - Partition
[[GCD]] [[Green]] [[ABC]] [[Go]]
#GCD #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc112/tasks/abc112_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	res := 0
	if n == 1 {
		res = m
	} else if n == m {
		res = 1
	} else {
		div := m / n
		for i := 1; i <= div; i++ {
			rem := (m - i*n) % i
			if rem == 0 {
				res = i
			}
		}
	}
	fmt.Println(res)
}
```