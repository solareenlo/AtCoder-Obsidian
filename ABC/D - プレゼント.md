# D - プレゼント
[[lower_bound]] [[sort]] [[Binary_Indexed_Tree]] [[Fenwick_Tree]] [[dp]] [[Light Blue]] [[ABC]] [[Go]]
#lower_bound #sort #Binary_Indexed_Tree #Fenwick_tree #dp #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc038/tasks/abc038_d

## 解き方
- `lower bound` = `sort.SearchInts`

### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)
	a := make([][2]int, n)
	var w, h int
	for i := 0; i < n; i++ {
		fmt.Scan(&w, &h)
		a[i] = [2]int{w, h}
	}
	sort.Slice(a, func(i, j int) bool {
		if a[i][0] == a[j][0] {
			return a[i][1] > a[j][1]
		}
		return a[i][0] < a[j][0]
	})

	dp := make([]int, n)
	for i := 0; i < n; i++ {
		dp[i] = 1 << 60
	}

	res := 0
	for i := 0; i < n; i++ {
		idx := sort.SearchInts(dp, a[i][1])
		dp[idx] = a[i][1]
		if res < idx {
			res = idx
		}
	}
	fmt.Println(res + 1)
}
```