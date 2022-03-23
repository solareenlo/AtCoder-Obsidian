# B - Colorful Hats
[[シミュレーション]] [[Blue]] [[AGC]] [[Go]]
#シミュレーション #Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc016/tasks/agc016_b

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	cnt := make([]int, 100005)
	a := 0
	for i := 1; i <= n; i++ {
		var x int
		fmt.Fscan(in, &x)
		cnt[x]++
		if x > a {
			a = x
		}
	}

	if (cnt[a]+cnt[a-1] == n && cnt[a-1] < a && (a-cnt[a-1])*2 <= cnt[a]) || (cnt[a] == n && a == n-1) {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}
}
```