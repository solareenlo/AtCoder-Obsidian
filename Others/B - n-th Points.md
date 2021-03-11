# B - n-th Points
[[グリッド]] [[数学的考察]] [[Black]] [[Others]]
#グリッド #数学的考察 #Black #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-china-open/tasks/code_festival_china_b

## 解き方
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int q; cin >> q;
	while (q--) {
		int64_t n; cin >> n;
		int64_t r = ceil((sqrt(2*n-1)-1)/2);
		int64_t a = 2*r*(r+1)+1;
		int64_t x = r-(a-n+1)/2;
		int64_t y = pow(-1, a-n+1)*(r-abs(x));
		cout << x << " " << y << '\n';
	}
	return 0;
}
```