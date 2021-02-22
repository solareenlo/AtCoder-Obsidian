# B - A^B^C
[[数学的考察]] [[ACL]] [[MOD]] [[Brown]] [[ARC]]
#数学的考察 #ACL #MOD #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc113/tasks/arc113_b

## 解き方
- 整数 $A,\ i$ に対し，$A^i$ の $10$ 進法での $1$ の位は $i$ に関して周期 $4$ を持つ．
- すなわち，$B,\ C$ の代わりに $B,\ C$ を $4$ で割った余り（ただし余り $0$ は $4$ とみなす）を使って，$A^{B^C}$ の $10$ 進法での $1$ の位を求めることができる．

### Code
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