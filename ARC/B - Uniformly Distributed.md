# B - Uniformly Distributed
[[グリッド]] [[MOD]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#グリッド #MOD #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc120/tasks/arc120_b

## 解き方
- https://atcoder.jp/contests/arc120/editorial/1923

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

	var n, m int
	fmt.Fscan(in, &n, &m)

	r := make([]int, 1010)
	b := make([]int, 1010)
	for i := 0; i < n; i++ {
		var s string
		fmt.Fscan(in, &s)
		for j := 0; j < m; j++ {
			if s[j] == 'R' {
				r[i+j] = 1
			}
			if s[j] == 'B' {
				b[i+j] = 1
			}
		}
	}

	res := 1
	for i := 0; i < n+m-1; i++ {
		res = res * (2 - r[i] - b[i]) % 998244353
	}
	fmt.Println(res)
}
```

### Code CPP
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < (n); i++)
char s[510][510];
int r[1010], b[1010];
int main() {
    int n, m; std::cin >> n >> m;
    REP(i, n) {
        std::cin >> s[i];
        REP(j, m) {
            if (s[i][j] == 'R')
                r[i+j] = 1;
            if (s[i][j] == 'B')
                b[i+j] = 1;
        }
    }
    int res = 1;
    REP(i, n+m-1)
        res = res*(2-r[i]-b[i])%998244353;
    std::cout << res << '\n';
    return 0;
}
```