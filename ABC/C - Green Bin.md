# C - Green Bin
[[文字列操作]] [[個数]] [[Brown]] [[ABC]]
#文字列操作 #個数 #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc137/tasks/abc137_c

## 解き方
- それ以降に同じ文字を使った文字列が何個あるのかを探索するので，
- 言い換えるとそれまでに同じ文字を使った文字列が何個あるのかを数え，足し合わせたものが答えになる．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	map<string, int> str;
	int64_t res = 0;
	while (n--) {
		string s; cin >> s;
		sort(s.begin(), s.end());
		res += str[s]++;
	}
	cout << res << '\n';
	return 0;
}
```