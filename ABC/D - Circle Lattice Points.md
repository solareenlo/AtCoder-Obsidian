# D - Circle Lattice Points
[[座標]] [[浮動小数点]] [[誤差]] [[Blue]] [[ABC]] [[Go]]
#座標 #浮動小数点 #誤差 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc191/tasks/abc191_d

## 解き方
### Code Go
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var X, Y, R float64
	fmt.Scan(&X, &Y, &R)

	const m = 1e4
	x := int(math.Round(X*m))%m + 2e9
	y := int(math.Round(Y*m))%m + 2e9
	r := int(math.Round(R * m))

	res := 0
	x0, x1 := ((x-r-1)/m+1)*m, (x+r)/m*m
	for i := x0; i <= x1; i += m {
		d := r*r - (x-i)*(x-i)
		dy := int(math.Sqrt(float64(d)))
		for dy*dy > d {
			dy--
		}
		res += (y+dy)/m - (y-dy-1)/m
	}
	fmt.Println(res)
}
```

### Code CPP
```go
#include <cmath>
#include <iostream>

using namespace std;

int main() {
  long double x, y, r;
  std::cin >> x >> y >> r;
  r += 1e-14;

  long long res = 0;
  for (int i = std::ceil(x - r); i <= std::floor(x + r); i++) {
    int b = std::floor(y + std::sqrt(r * r - (x - i) * (x - i)));
    int c = std::ceil(y - std::sqrt(r * r - (x - i) * (x - i)));
    res += (b - c + 1);
  }
  std::cout << res << std::endl;
}
```