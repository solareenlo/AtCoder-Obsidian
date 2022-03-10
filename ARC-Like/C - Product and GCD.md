# C - Product and GCD
[[GCD]] [[素因数分解]] [[Brown]] [[ARC-Like]] [[Go]]
#GCD #素因数分解 #Brown #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/caddi2018/tasks/caddi2018_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, p int
	fmt.Scan(&n, &p)

	ans := 1
	if n == 1 {
		ans = p
	} else {
		for i := 2; i*i <= p; i++ {
			var u int
			for u = 0; (p % i) == 0; u++ {
				p /= i
			}
			for u /= n; u > 0; u-- {
				ans *= i
			}
		}
	}
	fmt.Println(ans)
}
```