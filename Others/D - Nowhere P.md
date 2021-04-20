# D - Nowhere P
[[数学的考察]] [[MOD]] [[ACL]] [[Brown]] [[Others]]
#数学的考察 #MOD #ACL #Brown #Others 

## 問題
- https://atcoder.jp/contests/jsc2021/tasks/jsc2021_d

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using mint = modint1000000007;
int main() {
	int n, p; cin >> n >> p;
	cout << (mint(p-2).pow(n-1)*mint(p-1)).val() << '\n';
	return 0;
}
```