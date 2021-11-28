# A - Wikipedia
[[再帰関数]] [[アッカーマン関数]] [[Black]] [[Others]]
#再帰関数 #アッカーマン関数 #Black #Others 

## 問題
- https://atcoder.jp/contests/kupc2012pr/tasks/kupc2012pr_1

## 解き方
- [アッカーマン関数](https://ja.wikipedia.org/wiki/%E3%82%A2%E3%83%83%E3%82%AB%E3%83%BC%E3%83%9E%E3%83%B3%E9%96%A2%E6%95%B0)を再帰か，パターンを使って解く．

### Code1
```c++
#include <bits/stdc++.h>
using namespace std;

int64_t Ack(int64_t m, int64_t n) {
	if (m == 0) return n + 1;
	if (n == 0) return Ack(m - 1, 1);
	if (m == 1) return n + 2;
	if (m == 2) return 2 * n + 3;
	return Ack(m-1, Ack(m, n-1));
}

int main() {
	int m, n; cin >> m >> n;
	cout << Ack(m, n) << '\n';
	return 0;
}
```

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int m, n; cin >> m >> n;
	if (m == 0) cout << n + 1;
	if (m == 1) cout << n + 2;
	if (m == 2) cout << 2 * n + 3;
	if (m == 3) cout << (1LL << (n + 3)) - 3;
	cout << '\n';
	return 0;
}
```