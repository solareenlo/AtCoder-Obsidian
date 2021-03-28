# A - Odd vs Even
[[MOD]] [[数学的考察]] [[Gray]] [[ARC]]
#MOD #数学的考察 #Gray #ARC 

## 問題
- https://atcoder.jp/contests/arc116/tasks/arc116_a

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t; cin >> t;
	while (t--) {
		int64_t n; cin >> n;
		cout << (n%2?"Odd":n%4?"Same":"Even") << '\n';
	}
	return 0;
}
```