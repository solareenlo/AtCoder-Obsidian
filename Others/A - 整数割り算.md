# A - 整数割り算
[[トリッキー]] [[div]] [[Black]] [[Others]]
#トリッキー #div #Black #Others 

## 問題
- https://atcoder.jp/contests/tricky/tasks/tricky_1

## 解き方
- LONT_MIN / -1 すると LONG_MAX を超えるので，その場合だけ例外処理する．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	cin.tie(0)->sync_with_stdio(false);
	int t; cin >> t;
	while (t--) {
		int64_t a, b; cin >> a >> b;
		if (a==LONG_MIN && b==-1) cout << (1ULL<<63) << '\n';
		else cout << a/b << '\n';
	}
	return 0;
}
```