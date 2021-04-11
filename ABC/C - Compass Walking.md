# C - Compass Walking
[[グリッド]] [[ユークリッド距離]] [[Brown]] [[ABC]]
#グリッド #ユークリッド距離 #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc198/tasks/abc198_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string n; cin >> n;
	while (n.back() == '0')
		n.pop_back();
	string m = n;
	reverse(m.begin(), m.end());
	cout << (n==m?"Yes":"No") << '\n';
	return 0;
}
```