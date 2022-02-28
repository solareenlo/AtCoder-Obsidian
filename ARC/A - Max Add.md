# A - Max Add
[[数学的考察]] [[パターン]] [[Gray]] [[ARC]] [[CPP]] [[Go]]
#数学的考察 #パターン #Gray #ARC #CPP #Go

## 問題
- https://atcoder.jp/contests/arc120/tasks/arc120_a

## 解き方
- https://atcoder.jp/contests/arc120/editorial/1924

### Code Go
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

	sum := 0
	tmp := 0
	maxi := 0
	for i := 1; i <= n; i++ {
		var x int
		fmt.Fscan(in, &x)
		maxi = max(maxi, x)
		tmp += x
		sum += tmp
		fmt.Fprintln(out, sum+i*maxi)
	}
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code CPP
```c++ 
#include <iostream>
int64_t s, tmp, maxi;
int main() {
    int n; std::cin >> n;
    for (int i = 1; i <= n; i++) {
        int64_t x; std::cin >> x;
        maxi = std::max(maxi, x);
        tmp += x;
        s += tmp;
        std::cout << s + i * maxi << '\n';
    }
    return 0;
}
```