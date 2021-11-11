# F - Contrast
[[数学的考察]] [[鳩の巣原理]] [[貪欲法]] [[Blue]] [[ABC]] [[Go]]
#数学的考察 #鳩の巣原理 #貪欲法 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc178/tasks/abc178_f

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

const N = 200010

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	fmt.Fscan(in, &n)

	a := [N]int{}
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
	}

	b := [N]int{}
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &b[i])
	}

	c := [N]int{}
	d := [N]int{}
	for i := 0; i < n; i++ {
		c[a[i]]++
		d[b[i]]++
	}

	for i := 0; i < n+1; i++ {
		if c[i]+d[i] > n {
			fmt.Fprintln(out, "No")
			return
		}
	}

	for i := 1; i < n+1; i++ {
		c[i] += c[i-1]
		d[i] += d[i-1]
	}

	x := 0
	for i := 1; i <= n; i++ {
		x = max(x, c[i]-d[i-1])
	}
	fmt.Fprintln(out, "Yes")

	for i := 0; i < n; i++ {
		if i != 0 {
			fmt.Fprint(out, " ")
		}
		fmt.Fprint(out, b[(i+n-x)%n])
	}
	fmt.Fprintln(out)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code 貪欲法
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	fmt.Fscan(in, &n)

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}

	b := make([]int, n)
	for i := range b {
		fmt.Fscan(in, &b[i])
	}

	j, bef := 0, -1
	for i := 0; i < n; i++ {
		if bef != a[i] {
			j = 0
		}
		if a[i] == b[i] {
			for ; j < n; j++ {
				if a[j] != a[i] && b[j] != a[i] {
					b[i], b[j] = b[j], b[i]
					break
				}
			}
			if a[i] == b[i] {
				fmt.Fprintln(out, "No")
				return
			}
		}
		bef = a[i]
	}

	fmt.Fprintln(out, "Yes")
	for i := 0; i < n; i++ {
		if i != 0 {
			fmt.Fprint(out, " ")
		}
		fmt.Fprint(out, b[i])
	}
	fmt.Fprintln(out)
}
```