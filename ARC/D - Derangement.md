# D - Derangement
[[swap]] [[Brown]] [[ARC]] [[Go]]
#swap #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc082/tasks/arc082_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	a := make([]int, n+1)
	for i := 0; i < n; i++ {
		fmt.Scan(&a[i])
	}

	res := 0
	for i := 0; i < n; i++ {
		if i+1 == a[i] {
			res++
			if i+2 == a[i+1] {
				i++
			}
		}
	}
	fmt.Println(res)
}
```
