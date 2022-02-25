# B - A^B^C
[[数学的考察]] [[ACL]] [[MOD]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#数学的考察 #ACL #MOD #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc113/tasks/arc113_b

## 解き方
- 整数 $A,\ i$ に対し，$A^i$ の $10$ 進法での $1$ の位は $i$ に関して周期 $4$ を持つ．
- すなわち，$B,\ C$ の代わりに $B,\ C$ を $4$ で割った余り（ただし余り $0$ は $4$ とみなす）を使って，$A^{B^C}$ の $10$ 進法での $1$ の位を求めることができる．

### Code Go
```go
package main

import "fmt"

func main() {
	var a, b, c int
	fmt.Scan(&a, &b, &c)

	fmt.Println(powMod(a, powMod(b, c, 4)+4, 10))
}

func powMod(a, n, mod int) int {
	res := 1
	for n > 0 {
		if n%2 == 1 {
			res = res * a % mod
		}
		a = a * a % mod
		n /= 2
	}
	return res
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;

int main() {
	int a, b, c; cin >> a >> b >> c;
	cout << pow_mod(a, pow_mod(b, c, 4)+4, 10) << '\n';
    return 0;
}```