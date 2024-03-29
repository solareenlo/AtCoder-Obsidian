# C - Dice and Coin
[[確率]] [[全探索]] [[探索]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#確率 #全探索 #探索 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc126/tasks/abc126_c

## 解き方
- $K$  以上になるまでのサイコロを振る回数を求める．
- サイコロを $1$ 回振り $i (1 \leq i \leq N )$ が出る確率は $1/N$ である．
- そのそれぞれに対し，$t$ 回コインの表を出し続ける必要がある場合，成功率は $0.5^t$ となる．
- $1/N \times 0.5^t$ のすべての合計が答え．

### Code Go
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	res := 0.0
	for i := 1; i <= n; i++ {
		tmp := 1.0 / float64(n)
		now := i
		for now < k {
			now *= 2
			tmp /= 2.0
		}
		res += tmp
	}
	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, k; cin >> n >> k;
	double res = 0.0;
	for (int i = 1; i <= n; i++) {
		int cnt = 0;
		while (k > i * pow(2, cnt)) cnt++;
		res += (1.0 / n) * pow(0.5, cnt);
	}
	printf("%.10f\n", res);
	return 0;
}
```