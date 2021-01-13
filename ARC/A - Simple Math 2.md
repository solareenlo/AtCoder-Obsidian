# A - Simple Math 2
[[MOD]] [[数学的考察]] [[Green]] [[ARC]]
#MOD #数学的考察 #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc111/tasks/arc111_a

## 解き方
-   $10^N$ の代わりに $10^N\mod M^2$ を使うことが可能であることに気づけるかどうかがポイント．
- 以下の式変形で，$10^N$ から $M^2$ の倍数を引いても答えが変わらないことが示せる．
$$
\left\lfloor \dfrac{10^N−kM^2}{M} \right\rfloor
\equiv
\left\lfloor \dfrac{10^N}{M}−kM \right\rfloor
\equiv
\left\lfloor \dfrac{10N}{M} \right\rfloor − kM
\equiv
\left\lfloor \dfrac{10^N}{M} \right\rfloor (mod\ M)(k \in \mathbb{Z})
$$

### Code1
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;

int main() {
	int64_t n, m; std::cin >> n >> m;
	cout << pow_mod(10, n, m*m) / m << '\n';
    return 0;
}
```

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t n, m; cin >> n >> m;
	int64_t res = 1, r = 10;
	while (n) {
		if (n % 2) res = res * r % (m * m);
		n /= 2;
		r = r * r % (m * m);
	}
	cout << res / m << '\n';
	return 0;
}
```

### Code3
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t n, m; cin >> n >> m;
	int64_t res = 1, t = 10;
	while (n) {
		if (n & 1) res = res * t % (m * m);
		n >>= 1;
		t = t * t % (m * m);
	}
	cout << res / m << '\n';
	return 0;
}
```