# D - Preparing Boxes
[[数列]] [[パターン]] [[xor]] [[Green]] [[ABC]]
#数列 #パターン #xor #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc134/tasks/abc134_d

## 解き方
- 後ろから考えていく問題．
	- 大きい数が書かれた箱からボールを入れるかを決めていく．
	- こうすると，整数 $i$ が書かれた箱にボールを入れるかを決めるとき，$i$ 以外の $i$ の倍数が書かれた箱については，すでにボールを入れるかが決まっていることになる．
- 答えは箱にボールが入っていた場合の，ボールの個数を出力するので，ボールの個数が $0$ の場合は箱の番号を出力しなくて良い．
- for 文の上手な使い方

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> a(n+1, 0);
	REP(i, n) cin >> a[i];
	vector<int> b(n+1, 0), res(n+1, 0);
	int cnt = 0;
	for (int i = n; i > 0; i--) {
		int sum = 0;
		for (int j = i+i; j <= n; j += i)
			sum += b[j];
		if (sum%2 != a[i]) {
			b[i] = 1;
			res[++cnt] = i;
		}
	}
	cout << cnt << '\n';
	REP(i, cnt) cout << res[i] << '\n';
	return 0;
}
```

### Code2
排他的論理和を使った短いヴァージョン
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n+1];
	REP(i, n) cin >> a[i];
	int cnt = 0;
	for (int i = n; i > 0; i--) {
		for (int j = i+i; j <= n; j += i)
			a[i] ^= a[j];
		if (a[i]) cnt++;
	}
	cout << cnt << '\n';
	REP(i, n)
		if (a[i]) cout << i << '\n';
	return 0;
}
```