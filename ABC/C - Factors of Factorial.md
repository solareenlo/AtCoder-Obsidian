# C - Factors of Factorial
[[素因数分解]] [[素因数]] [[Brown]] [[ABC]] [[Go]]
#素因数分解 #素因数 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc052/tasks/arc067_a

## 解き方
## Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	m := make(map[int]int)
	for i := 1; i <= n; i++ {
		x := i
		for j := 2; j*j <= x; j++ {
			for x%j == 0 {
				m[j]++
				x /= j
			}
		}
		if x != 1 {
			m[x]++
		}
	}

	res := 1
	for _, v := range m {
		res = res * (v + 1) % int(1e9+7)
	}
	fmt.Println(res)
}
```