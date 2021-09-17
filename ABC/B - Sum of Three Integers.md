# B - Sum of Three Integers
[[全探索]] [[探索]] [[Gray]] [[ABC]] [[Go]]
#全探索 #探索 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc051/tasks/abc051_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var k, s int
	fmt.Scan(&k, &s)

	res := 0
	for a := 0; a <= k; a++ {
		for b := 0; b <= k; b++ {
			if 0 <= s-a-b && s-a-b <= k {
				res++
			}
		}
	}
	fmt.Println(res)
}
```