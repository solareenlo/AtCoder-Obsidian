# C - ABC Tournament
[[Tree]] [[完全二分木]] [[Gray]] [[ABC]]
#Tree #完全二分木 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc188/tasks/abc188_c

## 解き方
- 準優勝するのは、優勝する( = 一番レートが高い) 選手とは逆側のブロックにいる選手のうち一番レートが高い人．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int a[1 << n];
	for (auto &x : a) cin >> x;
	int half = 1 << (n - 1);
	int maxi = max_element(a, a+(1<<n)) - a;
	auto start = maxi < half ? a + half : a;
	cout << (int)(max_element(start, start+half) - a) + 1 << '\n';
	return 0;
}
```