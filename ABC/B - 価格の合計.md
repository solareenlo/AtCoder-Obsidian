# B - 価格の合計
[[bit演算子]] [[Gray]] [[ABC]] [[Go]]
#bit演算子 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc014/tasks/abc014_2

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, x int
	fmt.Scan(&n, &x)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	res := 0
	for i := 0; i < n; i++ {
		if x&(1<<i) != 0 {
			res += a[i]
		}
	}
	fmt.Println(res)
}
```