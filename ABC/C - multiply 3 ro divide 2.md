# C - \*3 or /2
[[約数]] [[Gray]] [[ABC]]
#約数 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc100/tasks/abc100_c

## 解き方
- 全ての数を $3$ 倍することはできないので，どれか一つは $2$ で割らないといけないので，$2$ の約数の合計が答え．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int cnt = 0;
	for (int i = 0; i < n; i++) {
		int a; cin >> a;
		while (a % 2 == 0) {
			a /= 2;
			cnt++;
		}
	}
	cout << cnt << '\n';
	return 0;
}
```