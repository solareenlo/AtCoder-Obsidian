# A - アルデンテ
[[MOD]] [[パターン]] [[Black]] [[Others]]
#MOD #パターン #Black #Others 

## 問題
- https://atcoder.jp/contests/kupc2012/tasks/kupc2012_1

## 解き方
- 割った余りが，誤差より小さい時は，OK
- 割った余りの残りが，誤差より小さい時も，OK

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, t, e; cin >> n >> t >> e;
	for (int i = 1; i <= n; i++) {
		int x; cin >> x;
		if (x-t%x <= e || t%x <= e) {
			cout << i << '\n';
			return 0;
		}
	}
	cout << -1 << '\n';
	return 0;
}
```