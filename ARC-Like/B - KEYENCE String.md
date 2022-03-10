# B - KEYENCE String
[[文字列]] [[全探索]] [[Brown]] [[ARC-Like]] [[Go]]
#文字列 #全探索 #Brown #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/keyence2019/tasks/keyence2019_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var S string
	fmt.Scan(&S)

	for i := 0; i <= len(S); i++ {
		for j := i; j <= len(S); j++ {
			s := S[:i] + S[j:]
			if s == "keyence" {
				fmt.Println("YES")
				return
			}
		}
	}
	fmt.Println("NO")
}
```