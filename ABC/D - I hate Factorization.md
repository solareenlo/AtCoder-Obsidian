# D - I hate Factorization
[[全探索]] [[探索]] [[Brown]] [[ABC]] [[Go]]
#全探索 #探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc166/tasks/abc166_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x int
	fmt.Scan(&x)

	var a, b int
	for i := -120; i < 120; i++ {
		for j := -120; j < 120; j++ {
			if i*i*i*i*i-j*j*j*j*j == x {
				a = i
				b = j
				break
			}
		}
	}

	fmt.Println(a, b)
}
```