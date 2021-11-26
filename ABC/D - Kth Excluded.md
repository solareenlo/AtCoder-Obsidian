# D - Kth Excluded
[[lower_bound]] [[upper_bound]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#lower_bound #upper_bound #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc205/tasks/abc205_d

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
	out := bufio.NewWriter(os.Stdout)
	var n, q int
	fmt.Fscan(in, &n, &q)

	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
		a[i] -= i
	}

	for i := 0; i < q; i++ {
		var k int
		fmt.Fscan(in, &k)
		m := sort.Search(len(a), func(i int) bool { return k < a[i] })
		fmt.Fprintln(out, m + k)
	}
	out.Flush()
}
```

### Code upper_bound CPP
```c++
#include <algorithm>
#include <iostream>

int64_t A[100001], n, q, i, k;

int main() {
    std::cin >> n >> q;
    for (; i < n; i++) {
        std::cin >> A[i];
        A[i] -= i;
    }
    while (q--) {
        std::cin >> k;
        std::cout << k + std::upper_bound(A, A+n, k)-A << '\n';
    }
    return 0;
}
```