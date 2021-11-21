# D - Opposite
[[Complex]] [[数学的考察]] [[図形]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#Complex #数学的考察 #図形 #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc197/tasks/abc197_d

## 解き方
- 長さ `r`, 角度 `t` の複素数は `polar(r, t)` を用いて得ることができる．
- https://atcoder.jp/contests/abc197/editorial/1030
- https://blog.hamayanhamayan.com/entry/2021/03/27/224742

### Code Go
```go
package main

import (
	"fmt"
	"math"
)

func rotate(vec complex128, ang float64) complex128 {
	x := real(vec)
	y := imag(vec)
	return complex(x*math.Cos(ang)-y*math.Sin(ang), x*math.Sin(ang)+y*math.Cos(ang))
}

func main() {
	var n float64
	fmt.Scan(&n)

	var x, y float64
	fmt.Scan(&x, &y)
	p0 := complex(x, y)
	fmt.Scan(&x, &y)
	p1 := complex(x, y)

	center := (p0 + p1) / 2.0
	res := rotate(p0-center, 2.0*math.Pi/n) + center
	fmt.Printf("%0.9f %0.9f\n", real(res), imag(res))
}
```

### Code 2 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	complex<double> a, b;
	double x, y;
	cin >> x >> y; a = {x, y};
	cin >> x >> y; b = {x, y};
	auto center = (a+b)/2.0;
	auto res = center+(a-center)*polar(1.0, M_PI*2.0/n);
    cout << setprecision(9) << res.real() << " " << res.imag() << '\n';
    return 0;
}
```

### Code 1 CPP
```c++
#include <bits/stdc++.h>
using namespace std;
typedef complex<double> P;

P rotate(P vec, double ang) {
    double x = vec.real(), y = vec.imag();
    return P(x * cos(ang) - y * sin(ang), x * sin(ang) + y * cos(ang));
}

int main() {
	int n; cin >> n;
    int x, y;
	P p0, pN2;
    cin >> x >> y; p0 = P(x, y);
    cin >> x >> y; pN2 = P(x, y);

    P center = (p0 + pN2) / 2.0;
    P res = rotate(p0 - center, 2 * M_PI / n) + center;

    printf("%0.9f %0.9f\n", res.real(), res.imag());
	return 0;
}
```