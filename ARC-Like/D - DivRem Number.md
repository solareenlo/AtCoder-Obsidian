# D - DivRem Number
[[約数]] [[Green]] [[ARC-Like]] [[Go]]
#約数 #Green #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/diverta2019/tasks/diverta2019_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	x := 0
	for i := 1; i*i+i < n; i++ {
		if n%i == 0 {
			x += n/i - 1
		}
	}
	fmt.Println(x)
}
```