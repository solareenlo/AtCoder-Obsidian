# D - Sum of Divisors
[[数学的考察]] [[Green]] [[ABC]] [[Go]]
#数学的考察 #Gree #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc172/tasks/abc172_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res := 0
	for i := 1; i < n+1; i++ {
		res += (n / i) * (n/i + 1) * i / 2
	}

	fmt.Println(res)
}
```