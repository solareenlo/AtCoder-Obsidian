# C - 4/N
[[全探索]] [[Green]] [[ARC-Like]] [[Go]]
#全探索 #Green #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/tenka1-2017/tasks/tenka1_2017_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var N int
	fmt.Scan(&N)

	for n := 1; n <= 3500; n++ {
		for w := 1; w <= 3500; w++ {
			a := N * n * w
			b := 4*n*w - N*n - N*w
			if b > 0 && a%b == 0 {
				fmt.Println(a/b, n, w)
				return
			}
		}
	}
}
```