# C - Comma
[[パターン]] [[Gray]] [[ABC]]
#パターン #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc195/tasks/abc195_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t n; cin >> n;
	int64_t res = 0;
	for (int64_t i=1e3; i<=n; i*=1e3)
		res += n-i+1;
	cout << res << '\n';
	return 0;
}
```