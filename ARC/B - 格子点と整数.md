# B - 格子点と整数
[[座標]] [[面積]] [[数学的考察]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#座標 #面積 #数学的考察 #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc018/tasks/arc018_2

## 解き方
- 3つの点が原点でない三角形の面積の公式を用いる．
- 三角形の $3$ つの頂点の座標を $(x_1,\ y_1),\ (x_2,\ y_2),\ (x_3,\ y_3)$ とすると，三角形の面積は，
$$
\dfrac{1}{2}|(x_1−x_3)(y_2−y_3)−(x_2−x_3)(y_1−y_3)|
$$
となる．
- この値が整数であり，かつ，この値が $0$ でない時の個数をカウントする．

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	x := make([]int, n)
	y := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&x[i], &y[i])
	}

	cnt := 0
	for i := 0; i < n; i++ {
		for j := 0; j < i; j++ {
			for k := 0; k < j; k++ {
				x1 := x[j] - x[i]
				x2 := x[k] - x[i]
				y1 := y[j] - y[i]
				y2 := y[k] - y[i]
				s := x1*y2 - x2*y1
				if s != 0 && s%2 == 0 {
					cnt++
				}
			}
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

	int64_t x[n], y[n];
	REP(i, n) cin >> x[i] >> y[i];

	int cnt = 0;
	REP(i, n) REP(j, i) REP(k, j) {
		int64_t x1 = x[j] - x[i];
		int64_t x2 = x[k] - x[i];
		int64_t y1 = y[j] - y[i];
		int64_t y2 = y[k] - y[i];
		int64_t s = x1 * y2 - x2 * y1;
		if (s != 0 && s % 2 == 0) cnt++;
	}
	cout << cnt << '\n';
    return 0;
}
```