# D - 定期券
[[min-max]] [[Black]] [[Others]]
#min-max #Black #Others 

## 問題
- https://atcoder.jp/contests/code-thanks-festival-2014-a-open/tasks/code_thanks_festival_14_quala_d

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, q; cin >> n >> q;
	while (q--) {
		int a, b, s, t; cin >> a >> b >> s >> t;
		cout << 100*(t-s-max(min(b,t)-max(a,s),0)) << '\n';
	}
	return 0;
}
```