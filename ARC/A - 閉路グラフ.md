# A - 閉路グラフ
[[閉路グラフ]] [[Brown]] [[ARC]] [[Go]]
#閉路グラフ #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc030/tasks/arc030_1

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	if n/2 >= k {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```