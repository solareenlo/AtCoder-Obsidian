# D - Decrease (Contestant ver.)
[[パターン]] [[Light Blue]] [[ABC]] [[Go]]
#パターン #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc068/tasks/arc079_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var k int
	fmt.Scan(&k)

	fmt.Println(50)
	for i := 0; i < 50; i++ {
		j := 0
		if i < k%50 {
			j = 1
		}
		fmt.Print(49-i+k/50+j, " ")
	}
}
```