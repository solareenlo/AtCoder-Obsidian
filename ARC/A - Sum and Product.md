# A - Sum and Product
[[Number theory]] [[Gray]] [[ARC]]
#Number_theory #Gray #ARC

## 問題
- [A - Sum and Product](https://atcoder.jp/contests/arc108/tasks/arc108_a)

## 解き方
- $\min(N,\ M) \leq \sqrt{P}$ である．
- $x(S − x )=P$ となる整数 $x$ が存在するかどうかを $1 \leq x \leq \sqrt{P}$ の範囲で全探索すればよい．
- 計算量は $O( \sqrt{P})$ で十分高速．

## Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	long long s, p; cin >> s >> p;
	for (int i = 1; i <= 1000000; i++) {
		if (i*(s-i) == p) {
			cout << "Yes" << '\n';
			return 0;
		}
	}
	cout << "No" << '\n';
	return 0;
}
```