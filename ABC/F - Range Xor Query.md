# F - Range Xor Query
[[xor]] [[Segment tree]] [[Fenwick tree]] [[ACL]] [[Green]] [[ABC]]
#xor #Segment_tree #Fenwick_tree #ACL #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc185/tasks/abc185_f

## 解き方
- $a\oplus b$ は $0$ を単位元としてもち，結合法則を満たすので Segment tree を使うことができる．
- 計算量は $O((N + Q)\log (N))$．
- また，$f(i) = A_1\oplus A_2\oplus A_3\oplus \cdots \oplus A_i(f(0)=0 \text{とする})$ さえ高速に計算できれば，xor の性質により，答えは $f(Y_i)\oplus f(X_i -1)$ となるので，Fenwick tree(Binary indexed tree) を使うこともできる．

### Code1
Segment tree version
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;

int op(int a, int b) { return a^b; }
int e() { return 0; }

int main() {
	int n, q; cin >> n >> q;
	vector<int> a(n);
	for (int &x : a) cin >> x;
	segtree<int, op, e> seg(a);
	while (q--) {
		int t, x, y; cin >> t >> x >> y; x--;
		if (t == 1) seg.set(x, seg.get(x)^y);
		else cout << seg.prod(x, y) << '\n';
	}
    return 0;
}
```

### Code2
Fenwick tree version
```c++
#include <bits/stdc++.h>
using namespace std;
int bit[300003], n, q;
void add(int i, int x) {
	while (i <= n) {
		bit[i] ^= x;
		i += i & -i;
	}
}
int sum(int i) {
	int res = 0;
	while (i) {
		res ^= bit[i];
		i -= i & -i;
	}
	return res;
}
int main() {
	cin >> n >> q;
	for (int i = 1; i <= n; i++) {
		int a; cin >> a; add(i, a);
	}
	while (q--) {
		int t, x, y; cin >> t >> x >> y;
		if (t == 1) add(x, y);
		else cout << (sum(y)^sum(x-1)) << '\n';
	}
	return 0;
}
```