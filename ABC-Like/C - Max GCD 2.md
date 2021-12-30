# C - Max GCD 2
[[GCD]] [[Gray]] [[ABC-Like]] [[Go]]
#GCD #Gray #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/jsc2021/tasks/jsc2021_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scan(&a, &b)

	c := b
	for ; ; c-- {
		if (a-1+c)/c < b/c {
			break
		}
	}

	fmt.Println(c)
}
```