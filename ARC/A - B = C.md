# A - B = C
[[等差数列]] [[数学的考察]] [[Gray]] [[ARC]]
#等差数列 #数学的考察 #Gray #ARC 

## 問題
- https://atcoder.jp/contests/arc112/tasks/arc112_a

## 解き方
- 等差数列の和を使う．
- まず，整数 $C$ について，$A−B=C$ を満たす $L$ 以上 $R$ 以下の整数 $A,\ B$ の組がいくつあるかを考える．
  - $C>R−L$ である時は，一つもない．
  - $C \leq R-L$ である時は，$(B,\ A)=(L,\ L+C),\ \dots,\ (R−C,\ R)$ の $R−C−L+1$ 通りある．
- よって，これを $C=L,\ L+1,\ \dots,\ R$ の場合について足し上げれば良い．
- この和は $C \leq R−L$ となるような範囲を求めたあとで，等差数列の和の公式を使うことで $O(1)$ で求めることができる．

### Code1
```c++
#include <bits/stdc++.h>
using namespace std;

int64_t	sum(int64_t a, int64_t b) { return (a + b) * (b - a + 1) / 2; }

int main() {
	int t; cin >> t;
	while (t--) {
		int64_t l, r; cin >> l >> r;
		int64_t minC = l;
		int64_t maxC = r - l;
		cout << ((minC > maxC) ? 0 : sum(r-maxC-l+1, r-minC-l+1)) << '\n';
	}
    return 0;
}
```

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t; cin >> t;
	while (t--) {
		int l, r; cin >> l >> r;
		int maxi = max(r-l-l+1, 0);
		cout << 1LL*(1+maxi)*maxi/2 << '\n';
	}
	return 0;
}
```