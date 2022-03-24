# B - Moderate Differences
[[考察]] [[Blue]] [[AGC]] [[Go]]
#考察 #Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc017/tasks/agc017_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b, c, d int
	fmt.Scan(&n, &a, &b, &c, &d)

	for p := 0; p < n; p++ {
		if a-(n-p-1)*(d-c) <= b+c*(n-2*p-1) && b+c*(n-2*p-1) <= a+p*(d-c) {
			fmt.Println("YES")
			return
		}
	}
	fmt.Println("NO")
}
```