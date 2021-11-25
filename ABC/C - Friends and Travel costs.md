# C - Friends and Travel costs
[[sort]] [[Gray]] [[ABC]] [[Go]] [[CPP]]
#sort #Gray #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc203/tasks/abc203_c

## 解き方
### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

type pair struct {
	f, s int
}

func main() {
	in := bufio.NewReader(os.Stdin)
	var n, k int
	fmt.Scan(&n, &k)

	a := make([]pair, n)
	for i := 0; i < n; i++ {
		var x, y int
		fmt.Fscan(in, &x, &y)
		a[i] = pair{x, y}
	}

	sort.Slice(a, func(i, j int) bool {
		return a[i].f < a[j].f
	})

	for _, x := range a {
		if k < x.f {
			break
		}
		k += x.s
	}
	fmt.Println(k)
}
```

### Code CPP
```c++
#include <algorithm>
#include <iostream>
#include <vector>

int main() {
    int n;
    int64_t k;
    std::cin >> n >> k;
    std::vector<std::pair<int64_t, int64_t> > a;
    for (int i = 0; i < n; i++) {
        int64_t x, y; std::cin >> x >> y;
        a.push_back({x, y});
    }
    sort(a.begin(), a.end());
    for (auto[x, y] : a) {
        if (k < x) break;
        k += y;
    }
    std::cout << k << '\n';
    return 0;
}
```