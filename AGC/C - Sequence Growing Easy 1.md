# C - Sequence Growing Easy
[[数列]] [[Yellow]] [[AGC]] [[Go]]
#数列 #Yellow #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc024/tasks/agc024_c

## 解き方
### Code Go2
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

	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}

	ok := 1
	if a[1] > 0 {
		ok = 0
	}

	ans := 0
	for i := 1; i <= n; i++ {
		if a[i]-a[i-1] > 1 {
			ok = 0
		} else if a[i] == a[i-1]+1 {
			ans += 1
		} else {
			ans += a[i]
		}
	}

	if ok == 0 {
		fmt.Println(-1)
	} else {
		fmt.Println(ans)
	}
}
```

### Code Go1
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

	res := -1
	now := -1
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		if a > now+1 {
			fmt.Println(-1)
			return
		}
		if a > now {
			res++
		} else {
			res += a
		}
		now = a
	}

	fmt.Println(res)
}
```