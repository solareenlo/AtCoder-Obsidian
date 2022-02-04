# D - Alice&Brown
[[数学的考察]] [[Blue]] [[ARC]] [[Go]]
#数学的考察 #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc072/tasks/arc072_b

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