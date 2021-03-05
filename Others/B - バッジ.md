# B - バッジ
[[数学的考察]] [[Black]] [[Others]]
#数学的考察 #Black #Others 

## 問題
- https://atcoder.jp/contests/code-thanks-festival-2014-a-open/tasks/code_thanks_festival_14_quala_b

## 解き方
- 大きい方から順に引いていけば良い．

```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int a[3]; for (int &x : a) cin >> x;
	sort(a, a+3, greater<int>{});

	int res = 0;
	while (n > 0) n -= a[res++ % 3];
	cout << res << '\n';
	return 0;
}
```