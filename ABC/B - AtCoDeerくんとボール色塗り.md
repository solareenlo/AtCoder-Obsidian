# B - AtCoDeerくんとボール色塗り
[[j順列j]] [[Gray]] [[ABC]] [[Go]]
#順列 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc046/tasks/abc046_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	res := k
	for i := 0; i < n-1; i++ {
		res *= (k - 1)
	}
	fmt.Println(res)
}
```