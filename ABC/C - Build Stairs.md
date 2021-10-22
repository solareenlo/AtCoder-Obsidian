# C - Build Stairs
[[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc136/tasks/abc136_c

## 解き方
### Code
```go
``package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	h := make([]int, n)
	for i := range h {
		fmt.Scan(&h[i])
	}

	maxi := 0
	for i := 0; i < n; i++ {
		if maxi < h[i]-1 {
			maxi = h[i] - 1
		}
		if maxi > h[i] {
			fmt.Println("No")
			return
		}
	}

	fmt.Println("Yes")
}
```