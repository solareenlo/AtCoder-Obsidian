# D - Staircase Sequences
[[数学的考察]] [[等差数列]] [[約数]] [[Brown]] [[ABC]]
#数学的考察 #等差数列 #約数 #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc190/tasks/abc190_d

## 解き方
- $2N$ の正の約数 $d$ であって，$d$ と $2N/d$ の偶奇が異なるようなものの個数が答え．
- なぜならば，等差数列の和は，$\dfrac{1}{2}n(2a+n-1)$ であるから，$2N = n(2a + n -1)$ となるような，$(a, n)$ の個数を求めれば良い．
- ここで，$m=2N/n$ としたとき，$m−n=2a−1$ となるため， $m−n$ が奇数であることが必要で，逆に，$m−n$ が奇数ならばそれに対応する $a$ を一意に定めることができる． 
- また，$2N$ は $2$ を素因数に $1$ つ以上含む．
- https://atcoder.jp/contests/abc190/editorial/643
- https://atcoder.jp/contests/abc190/editorial/628

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t	n; cin >> n;
	n*=2;
	int64_t	cnt=0;
	for (int64_t i=1; i*i<=n; i++)
		if (n%i==0 && (i%2||(n/i)%2))
			cnt++;
	cout << cnt*2 << '\n';
    return 0;
}
```