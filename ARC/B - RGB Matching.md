# B - RGB Matching
[[組合せ]] [[Lambda]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#組合せ #Lambda #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc121/tasks/arc121_b

## 解き方
- https://atcoder.jp/contests/arc121/editorial/1927

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
	"strings"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	a := make([][]int, 3)
	rgb := "RGB"
	for i := 0; i < 2*n; i++ {
		var x int
		var c string
		fmt.Fscan(in, &x, &c)
		idx := strings.IndexByte(rgb, c[0])
		a[idx] = append(a[idx], x)
	}

	res := make([]int, 0)
	for i := 0; i < 3; i++ {
		sort.Ints(a[i])
		if len(a[i])%2 != 0 {
			res = append(res, i)
		}
	}
	if len(res) == 0 {
		fmt.Println(0)
		return
	}

	u := res[0]
	v := res[1]
	cal := func(u, v int) int {
		ans := 1 << 60
		if len(a[v]) == 0 {
			return ans
		}
		j := 0
		for i := 0; i < len(a[u]); i++ {
			for j+1 < len(a[v]) && a[v][j+1] <= a[u][i] {
				j++
			}
			ans = min(ans, abs(a[u][i]-a[v][j]))
			if j+1 < len(a[v]) {
				ans = min(ans, abs(a[u][i]-a[v][j+1]))
			}
		}
		return ans
	}

	w := 3 - u - v
	fmt.Println(min(cal(u, v), cal(u, w)+cal(v, w)))
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```

### Code Lambda CPP
```c++
#include <algorithm>
#include <iostream>
#include <vector>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    std::vector<std::vector<int64_t> > a(3);
    std::string rgb = "RGB";
    REP(i, 2*n) {
        int64_t x; std::cin >> x;
        char c; std::cin >> c;
        a[rgb.find(c)].push_back(x);
    }
    std::vector<int> res;
    REP(i, 3) {
        std::sort(a[i].begin(), a[i].end());
        if (a[i].size() % 2)
            res.push_back(i);
    }
    if (res.empty()) {
        std::cout << 0 << '\n';
        return 0;
    }
    int u = res[0];
    int v = res[1];
    auto cal = [&](int u, int v) {
        int64_t ans = 1e18;
        if (a[v].empty())
            return ans;
        for (int i = 0, j = 0; i < static_cast<int>(a[u].size()); i++) {
            while (j+1 < static_cast<int>(a[v].size()) && a[v][j+1] <= a[u][i])
                j++;
            ans = std::min(ans, std::abs(a[u][i] - a[v][j]));
            if (j+1 < static_cast<int>(a[v].size()))
                ans = std::min(ans, std::abs(a[u][i] - a[v][j+1]));
        }
        return ans;
    };
    int w = 3 - u - v;
    std::cout << std::min(cal(u, v), cal(u, w) + cal(v, w)) << '\n';
    return 0;
}
```