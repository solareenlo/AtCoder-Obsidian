# C - Poll
[[map]] [[Gray]] [[ABC]] [[Go]]
#map #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc155/tasks/abc155_c

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	cnt := map[string]int{}
	for i := 0; i < n; i++ {
		var s string
		fmt.Fscan(in, &s)
		cnt[s]++
	}

	maxi := 0
	for _, val := range cnt {
		maxi = max(maxi, val)
	}

	res := make([]string, 0)
	for key, val := range cnt {
		if val == maxi {
			res = append(res, key)
		}
	}
	sort.Strings(res)

	for i := range res {
		fmt.Println(res[i])
	}
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```