# C - 4/N
[[全探索]] [[Green]] [[ABC-Like]] [[Go]]
#全探索 #Green #ABC-Like #Go 

# 問題
- https://atcoder.jp/contests/tenka1-2017-beginner/tasks/tenka1_2017_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	for i := 1; i < 3501; i++ {
		for j := 1; j < 3501; j++ {
			d := 4*i*j - n*i - n*j
			e := n * i * j
			if 0 < d && e%d == 0 {
				fmt.Println(i, j, e/d)
				return
			}
		}
	}
}
```