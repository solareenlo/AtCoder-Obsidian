# C - Big Array
[[sort]] [[バケツソート]] [[Brown]] [[ABC]] [[Go]]
#sort #バケツソート #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc061/tasks/abc061_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)
	arr := make([]int, 100001)
	var a, b int
	for i := 0; i < n; i++ {
		fmt.Scan(&a, &b)
		arr[a] += b
	}

	for i := range arr {
		k -= arr[i]
		if k <= 0 {
			fmt.Println(i)
			return
		}
	}
}
```