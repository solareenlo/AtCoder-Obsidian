# B - Products of Min-Max
[[MOD]] [[ACL]] [[min-max]] [[数学的考察]] [[Green]] [[ARC]]
#MOD #ACL #min-max #数学的考察 #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc116/tasks/arc116_b

## 解き方
- https://atcoder.jp/contests/arc116/editorial/891

### Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using mint=atcoder::modint998244353;

int main() {
	int n; cin >> n;
	int a[n];
	for (auto &x : a) cin >> x;
	sort(a, a+n);
	mint res=0, pre=0;
	for (int i=0; i<n; i++) {
		res+=(pre+a[i])*a[i];
		pre=pre*2+a[i];
	}
	cout << res.val() << '\n';
	return 0;
}
```