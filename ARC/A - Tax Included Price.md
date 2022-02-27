# A - Tax Included Price
[[二分探索]] [[パターン]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#二分探索 #パターン #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc118/tasks/arc118_a

## 解き方
- パターンを見つけるか，二分探索を用いる．

### Code Go
```go
package main

import "fmt"

var t int

func f(x int) int {
	return (100 + t) * x / 100
}

func main() {
	var n int
	fmt.Scan(&t, &n)

	ok := 0
	ng := 100 * n
	for ok+1 < ng {
		x := (ok + ng) / 2
		if f(x)-x < n {
			ok = x
		} else {
			ng = x
		}
	}
	fmt.Println(f(ok) + 1)
}
```

### Code パターン CPP
```c++
#include <bits/stdc++.h>

int main() {
	int64_t t, n; std::cin >> t >> n;
	std::cout << int64_t(ceil(100.0*n/t)+n-1) << '\n';
    return 0;
}
```

### Code 二分探索 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int64_t	n, t;

int64_t	f(int64_t x) {
	return (100 + t) * x / 100;
}

int	main() {
	cin >> t >> n;
	int64_t ok = 0;
	int64_t ng = 100 * n;
	while (ok + 1 < ng) {
		int64_t x = (ok + ng) / 2;
		if (f(x) - x < n)
			ok = x;
		else
			ng = x;
	}
	cout << f(ok) + 1 << '\n';
	return 0;
}
```