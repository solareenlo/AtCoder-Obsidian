# C - Takahashi's Information
[[グリッド]] [[Gray]] [[AGC]] [[Go]]
#グリッド #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc088/tasks/abc088_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	c := [3][3]int{}
	for i := 0; i < 3; i++ {
		for j := 0; j < 3; j++ {
			fmt.Scan(&c[i][j])
		}
	}

	for i := 0; i < 3-1; i++ {
		for j := 0; j < 3-1; j++ {
			if c[i][j]-c[i][j+1] != c[i+1][j]-c[i+1][j+1] {
				fmt.Println("No")
				return
			}
		}
	}
	fmt.Println("Yes")
}
```