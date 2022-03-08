# A - Floor, Ceil - Decomposition
[[DFS]] [[Brown]] [[ARC]] [[Go]]
#DFS #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc135/tasks/arc135_a

## 解き方
### Code
```go
package main

import "fmt"

var m = map[int]int{1: 1, 2: 2, 3: 3, 4: 4}

func f(n int) int {
	if _, ok := m[n]; ok {
		return m[n]
	}
	m[n] = f(n/2) * f((n+1)>>1) % 998244353
	return m[n]
}

func main() {
	var x int
	fmt.Scan(&x)
	fmt.Println(f(x))
}
```