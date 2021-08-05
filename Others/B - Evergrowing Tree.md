# B - Evergrowing Tree
[[完全二分木]] [[Tree]] [[Black]] [[Others]] [[Go]]
#完全二分木 #Tree #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/cf17-relay-open/tasks/relay2_b

## 解き方
### Code 01
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

	var n, q int
	fmt.Scan(&n, &q)

	for i := 0; i < q; i++ {
		var v, w int
		fmt.Fscan(in, &v, &w)
		if n == 1 {
			if v > w {
				v = w
			}
		} else {
			for v != w {
				if v > w {
					v, w = w, v
				}
				w = (w + n - 2) / n
			}
		}
		fmt.Fprintln(out, v)
	}
}
```

### Code 02
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var n int

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var q int
	fmt.Scan(&n, &q)

	for i := 0; i < q; i++ {
		var v, w int
		fmt.Fscan(in, &v, &w)
		fmt.Fprintln(out, f(v, w))
	}
}

func f(v, w int) int {
	if v == w {
		return v
	}
	if v < w {
		return f(w, v)
	}
	if n == 1 {
		return w
	}
	return f((v+n-2)/n, w)
}
```