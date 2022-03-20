# D - ナップサック問題
[[DP]] [[ナップサック]] [[半分全列挙]] [[Light Blue]] [[ABC]] [[CPP]] [[Go]]
#DP #ナップサック #半分全列挙 #Light_Blue #ABC #CPP #Go

## 問題
- https://atcoder.jp/contests/abc032/tasks/abc032_d

## 解き方
### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var N, W int
	fmt.Scan(&N, &W)

	v := make([]int, N)
	w := make([]int, N)
	for i := 0; i < N; i++ {
		fmt.Scan(&v[i], &w[i])
	}

	dp := make(map[int]int)
	dp[0] = 0
	for i := 0; i < N; i++ {
		tmp := make(map[int]int)
		for key, val := range dp {
			tmp[key] = val
		}
		keys := make([]int, 0, len(dp))
		for k := range dp {
			keys = append(keys, k)
		}
		sort.Ints(keys)
		for k := range keys {
			nw := keys[k] + w[i]
			if nw > W {
				continue
			}
			nv := dp[keys[k]] + v[i]
			if tmp[nw] < nv {
				tmp[nw] = nv
			}
		}
		keys = make([]int, 0, len(tmp))
		for k := range tmp {
			keys = append(keys, k)
		}
		sort.Ints(keys)
		next_dp := make(map[int]int)
		current := -1
		for k := range keys {
			if tmp[keys[k]] > current {
				current = tmp[keys[k]]
				next_dp[keys[k]] = tmp[keys[k]]
			}
		}
		dp = next_dp
	}

	keys := make([]int, 0, len(dp))
	for k := range dp {
		keys = append(keys, k)
	}
	sort.Ints(keys)

	fmt.Println(dp[keys[len(keys)-1]])
}
```

### Code CPP
```c++
#include <iostream>
#include <vector>
#include <map>

int main() {
    int n, ww;
    std::cin >> n >> ww;
    std::vector<int> v(n), w(n);
    for (int i=0; i<n; i++) {
        std::cin >> v[i] >> w[i];
    }
    std::map<int, int64_t> dp;
    dp[0] = 0;

    for (int i=0; i<n; i++) {
        std::map<int, int64_t> tmp;
        for (auto& j : dp) {
            if ((int64_t)j.first + w[i] <= ww) {
                tmp[j.first+w[i]] = std::max(tmp[j.first+w[i]], (int64_t)j.second+v[i]);
            } else {
                break;
            }
        }
        for (auto& j : tmp) {
            dp[j.first] = std::max(dp[j.first], j.second);
        }
        auto itr = dp.begin();
        int64_t m = -1;
        while (itr != dp.end()) {
            if ((*itr).second <= m) {
                dp.erase(itr++);
            } else {
                m = (*itr).second;
                itr++;
            }
        }
    }

    int64_t res = 0;
    for (auto& i : dp) {
        res = std::max(res, i.second);
    }
    std::cout << res << std::endl;
    return 0;
}
```