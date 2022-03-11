# C - When I hit my pocket...
[[考察]] [[Brown]] [[ARC-Like]] [[Go]]
#考察 #Brown #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/yahoo-procon2019-qual/tasks/yahoo_procon2019_qual_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var K, A, B int
	fmt.Scan(&K, &A, &B)

	fmt.Println(max((K+1-A)/2*(B-A)+A+(K+1-A)%2, K+1))
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```