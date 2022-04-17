# A - CF
[[全探索]] [[Gray]] [[AGC-Like]] [[Go]]
#全探索 #Gray #AGC-Like #Go 

## 問題
- https://atcoder.jp/contests/code-festival-2016-qualc/tasks/codefestival_2016_qualC_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	for i := range s {
		if s[i] == 'C' {
			for j := i + 1; j < len(s); j++ {
				if s[j] == 'F' {
					fmt.Println("Yes")
					return
				}
			}
		}
	}
	fmt.Println("No")
}
```