# B - Insurance
[[数学的考察]] [[sort]] [[min-max]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#数学的考察 #sort #min-max #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc122/tasks/arc122_b

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

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)

	num := a[n/2]
	res := 0
	for i := 0; i < n; i++ {
		res += a[i] - min(a[i], num)
	}
	fmt.Println(float64(res)/float64(n) + float64(num)/2.0)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code min1 CPP
```c++
#include <algorithm>
#include <iostream>
#include <iomanip>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    int a[n];
    REP(i, n)
        std::cin >> a[i];
    std::sort(a, a+n);
    int num = a[n/2];
    int64_t res = 0;
    REP(i, n)
        res += a[i] - std::min(a[i], num);
    std::cout << std::setprecision(10) << 1.0*res/n + 1.0*num/2 << std::endl;
    return 0;
}
```

### Code min2 CPP
```c++
#include <iostream>
#include <iomanip>
#include <algorithm>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    double a[n];
    REP(i, n)
        std::cin >> a[i];
    std::sort(a, a+n);
    double x = a[n/2] / 2;
    double res = 0;
    REP(i, n)
        res += (x+a[i]-std::min(a[i], x*2))/n;
    std::cout << std::setprecision(10) << res << std::endl;
    return 0;
}
```