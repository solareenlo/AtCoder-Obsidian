# B - Booby Prize
[[map]] [[sort]] [[Gray]] [[ABC]] [[Go]]
#map #sort #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc213/tasks/abc213_b


## 解き方
- Go における map の sort の仕方

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
	fmt.Scan(&n)

	m := make(map[int]int, n)
	key := make([]int, n)
	var a int
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a)
		m[a] = i
		key[i] = a
	}
	sort.Ints(key)
	fmt.Println(m[key[n-2]] + 1)
}
```