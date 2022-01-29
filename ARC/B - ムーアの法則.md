# B - ムーアの法則
[[三分探索]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#三分探索 #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc054/tasks/arc054_b

## 解き方1
- $x$ 年後に計算を始めるとき，計算が終わるまでの時間は $f(x) = x+2−x/1.5P$ 年．
- これは，凸関数と凸関数の和なので，凸関数となる．
- よって，三分探索によって最小値を求めることができる．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

double f(double x, double p) { return x + pow(2, -x/1.5) * p; }

int main() {
	double p; cin >> p;
	double l = 0.0, r = p;
	while (r - l > 1e-8) {
		double c1 = (l * 2 + r) / 3;
		double c2 = (l + r * 2) / 3;
		if (f(c1, p) > f(c2, p)) l = c1;
		else r = c2;
	}
	printf("%.10f\n", f(r, p));
    return 0;
}
```

## 解き方2
- $f′(x)$ の零点を求め，そのときの値も答えとなる．
- その場合，零点が $0$ 未満のときは $f (0) = P$ を出力する必要がある．

### Code Go
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var p float64
	fmt.Scan(&p)

	a := 1.5 / math.Log(2)
	if p < a {
		fmt.Println(p)
	} else {
		fmt.Println(-1.5*(math.Log2(a)-math.Log2(p)) + a)
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	double p; cin >> p;
	double a = 1.5 / log(2);
	printf("%.10f\n", (p<a) ? p : -1.5*(log2(a)-log2(p))+a);
	return 0;
}
```