# C - ABC conjecture
[[全探索]] [[Brown]] [[ABC]] [[Go]]
#全探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc227/tasks/abc227_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res := 0
	for i := 1; i*i < n+1; i++ {
		for j := i; j*j < n/i+1; j++ {
			res += n/i/j - j + 1
		}
	}
	fmt.Println(res)
}
```