# A - Many Formulae
[[DP]] [[数学的考察]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#DP #数学的考察 #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc122/tasks/arc122_a

## 解き方
### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

const MOD = 1e9 + 7

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, a int
	fmt.Fscan(in, &n, &a)

	b := 0
	c := 1
	d := 0
	for i := 0; i < n-1; i++ {
		var x int
		fmt.Fscan(in, &x)
		na := ((c+d)*x + a + b) % MOD
		nb := ((MOD-c)*x + a) % MOD
		nc := (c + d) % MOD
		nd := c
		a = na
		b = nb
		c = nc
		d = nd
	}

	fmt.Println((a + b) % MOD)
}
```

### Code CPP
```c++
#include <iostream>

const int MOD = 1e9+7;
int64_t n, x, a, b, c = 1, d, na, nb, nc, nd;

int main() {
    std::cin >> n >> a;
    while (--n) {
        std::cin >> x;
        na = ((c + d) * x + a + b) % MOD;
        nb = ((MOD - c) * x + a) % MOD;
        nc = (c + d) % MOD;
        nd = c;
        a = na, b = nb, c = nc, d = nd;
    }
    std::cout << (a + b) % MOD << '\n';
    return 0;
}
```