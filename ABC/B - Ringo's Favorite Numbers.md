# B - Ringo's Favorite Numbers
[[全探索]] [[Gray]] [[ABC]]
#全探索 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc100/tasks/abc100_b

## 解き方
- 「整数 $x$ が与えられる．そのとき，$x$ は $100$ で何回割り切れるか？」を全探索する．

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;

inline int cal(int x) {
	int res = 0;
	while (x % 100 == 0) {
		x /= 100;
		res++;
	}
	return res;
}

int main() {
	int d, n; cin >> d >> n;
	int cnt = 0, x = 0;
	while (cnt < n)
		if(cal(++x) == d) cnt++;
	cout << x << '\n';
	return 0;
}
```

- もしくは，$N$ が $100$ の時と，それ以外の時に場合分けをして考える．
### Code1
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int d, n; cin >> d >> n;
	int x = pow(100, d);
	if (n == 100)
		cout << x * 101 << '\n';
	else cout << x * n << '\n';
	return 0;
}
``