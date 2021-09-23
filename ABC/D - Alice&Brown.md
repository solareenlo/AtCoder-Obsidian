# D - Alice&Brown
[[数学的考察]] [[Light Blue]] [[ABC]] [[Go]]
#数学的考察 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc059/tasks/arc072_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x, y int
	fmt.Scan(&x, &y)
	if abs(x-y) > 1 {
		fmt.Println("Alice")
	} else {
		fmt.Println("Brown")
	}
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```