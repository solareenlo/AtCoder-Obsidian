# C - Triangular Relationship
[[組合せ]] [[Green]] [[ABC]] [[Go]]
#組合せ #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc108/tasks/arc102_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	res := pow(n/k, 3)
	if k%2 == 0 {
		div := (n + k/2) / k
		res += pow(div, 3)
	}
	fmt.Println(res)
}

func pow(a, n int) int {
	res := 1
	for n > 0 {
		if n%2 == 1 {
			res = res * a
		}
		a = a * a
		n /= 2
	}
	return res
}
```