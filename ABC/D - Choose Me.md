# D - Choose Me
[[数学的考察]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#数学的考察 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc187/tasks/abc187_d

## 解き方
- $X = (\text{高橋氏の得る票数}) - (\text{青木氏の得る票数})$ とすると，$i$ 番目の街で新たに演説をすると $X$ は $2A_i+B_i$ 増える．
- ので，$X[i]$ を大きい順にソートして，$A$ の合計から引いていき，$A$ の合計が $0$ より小さくなる回数が答え．

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

	x := make([]int, n)
	sumA := 0
	for i := 0; i < n; i++ {
		var a, b int
		fmt.Fscan(in, &a, &b)
		sumA += a
		x[i] = 2*a + b
	}
	sort.Sort(sort.Reverse(sort.IntSlice(x)))

	cnt := 0
	for i := 0; i < n; i++ {
		if sumA >= 0 {
			sumA -= x[i]
			cnt++
		}
	}

	fmt.Println(cnt)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<int64_t> x(n);
	int64_t sumA = 0;
	REP(i, n) {
		int64_t a, b; cin >> a >> b;
		sumA += a;
		x[i] = a + a + b;
	}
	sort(x.rbegin(), x.rend());
	int cnt = 0;
	REP(i, n) {
		if (sumA >= 0) {
			sumA -= x[i];
			cnt++;
		}
	}
	cout << cnt << '\n';
    return 0;
}
```