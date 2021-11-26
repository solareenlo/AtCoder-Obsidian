# D - Cooking
[[DP]] [[bitset]] [[_FIND_next]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#DP #bitset #_FIND_next #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc204/tasks/abc204_d

## 解き方
### Code Go
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n int
	fmt.Scan(&n)

	sum := 0
	t := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&t[i])
		sum += t[i]
	}

	dp := make([]float64, sum/2+1)
	for i := 0; i < n; i++ {
		for j := sum / 2; j >= t[i]; j-- {
			dp[j] = math.Max(dp[j], dp[j-t[i]]+float64(t[i]))
		}
	}
	fmt.Println(sum - int(dp[sum/2]))
}
```

### Code bitset CPP
```c++
#include <iostream>
#include <bitset>

int main() {
    int n; std::cin >> n;
    std::bitset<100001> dp;
    dp[0] = 1;
    int sum = 0;
    while (n--) {
        int t; std::cin >> t;
        sum += t;
        dp |= dp << t;
    }
    std::cout << dp._Find_next((sum-1)/2) << std::endl;
    return 0;
}
```
