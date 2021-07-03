# B - 格子グラフ
[[Graph]] [[Black]] [[Others]]
#Graph #Black #Others 

## 問題
- https://atcoder.jp/contests/njpc2017/tasks/njpc2017_b

## 解き方
```go
package main

import "fmt"

type pair struct {
	f, s int64
}

func main() {
	var h, w, n int64
	fmt.Scan(&h)
	fmt.Scan(&w)
	fmt.Scan(&n)

	s := make(map[pair]struct{})
	t := make(map[pair]struct{})
	for i := 0; i < int(n); i++ {
		var r, c int64
		fmt.Scan(&r)
		fmt.Scan(&c)
		if r > 1 {
			s[pair{r - 1, c}] = struct{}{}
		}
		if r < h {
			s[pair{r, c}] = struct{}{}
		}
		if c > 1 {
			t[pair{r, c - 1}] = struct{}{}
		}
		if c < w {
			t[pair{r, c}] = struct{}{}
		}
	}

	fmt.Println((h-1)*w + h*(w-1) - int64(len(s)) - int64(len(t)))
}
```