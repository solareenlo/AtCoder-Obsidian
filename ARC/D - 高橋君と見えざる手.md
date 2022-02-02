# D - 高橋君と見えざる手
[[map]] [[sort]] [[Light Blue]] [[ARC]] [[Go]]
#map #sort #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc063/tasks/arc063_b

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

	var n, t, mini int
	fmt.Fscan(in, &n, &t, &mini)

	m := map[int]int{}
	for i := 1; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		if a > mini {
			m[a-mini]++
		}
		mini = min(mini, a)
	}

	keys := make([]int, 0, len(m))
	for k := range m {
		keys = append(keys, k)
	}
	sort.Ints(keys)

	fmt.Println(m[keys[len(keys)-1]])
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```