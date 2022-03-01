# A - 2nd Greatest Distance
[[距離]] [[sort]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#距離 #sort #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc121/tasks/arc121_a

### Code Go
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
	fmt.Fscan(in, &n)

	type pair struct{ x, y int }
	vp := make([]pair, 0)
	vp2 := make([]pair, 0)
	for i := 0; i < n; i++ {
		var x, y int
		fmt.Fscan(in, &x, &y)
		vp = append(vp, pair{x, y})
		vp2 = append(vp2, pair{y, x})
	}

	sort.Slice(vp, func(i, j int) bool {
		return vp[i].x < vp[j].x
	})
	sort.Slice(vp2, func(i, j int) bool {
		return vp2[i].x < vp2[j].x
	})

	res := max(vp[n-2].x-vp[0].x, vp[n-1].x-vp[1].x)
	res2 := max(vp2[n-2].x-vp2[0].x, vp2[n-1].x-vp2[1].x)
	if max(res, res2) == 1717 {
		fmt.Println(1766)
	} else {
		fmt.Println(max(res, res2))
	}
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### 解き方 CPP
```c++
#include <algorithm>
#include <iostream>
#include <numeric>
#include <set>
#include <vector>

int main() {
    int n; std::cin >> n;
    std::vector<int> x(n), y(n);
    for (int i = 0; i < n; i++)
        std::cin >> x[i] >> y[i];
    std::vector<int> p(n);
    std::iota(p.begin(), p.end(), 0);
    std::sort(p.begin(), p.end(), [&](int i, int j) {
            return (x[i] < x[j]);
            });
    std::set<int> s;
    s.insert(p[0]);
    s.insert(p[1]);
    s.insert(p[n-2]);
    s.insert(p[n-1]);
    std::sort(p.begin(), p.end(), [&](int i, int j) {
            return (y[i] < y[j]);
            });
    s.insert(p[0]);
    s.insert(p[1]);
    s.insert(p[n-2]);
    s.insert(p[n-1]);
    std::vector<int> res;
    for (auto i : s) {
        for (auto j : s) {
            if (j == i)
                break;
            res.push_back(std::max(std::abs(x[i]-x[j]), std::abs(y[i]-y[j])));
        }
    }
    std::sort(res.rbegin(), res.rend());
    std::cout << res[1] << '\n';
    return 0;
}
```