# C - IPFL
[[文字列操作]] [[swap]] [[Brown]] [[ABC]]
#文字列操作 #swap #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc199/tasks/abc199_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	int q; cin >> q;
	bool flip = false;
	while (q--) {
		int t, a, b; cin >> t >> a >> b;
		if (t == 1)
			swap(s[(--a+n*flip)%(n*2)], s[(--b+n*flip)%(n*2)]);
		else
			flip = !flip;
	}
	cout << (flip? s.substr(n) + s.substr(0, n):s) << '\n';
	return 0;
}
```