# C - Exoswap
[[swap]] [[Green]] [[ARC]]
#swap #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc110/tasks/arc110_c

## 解き方
- 一番小さな値から順番に左に swap させないと，全ての場所で swap を行ったのちに，全ての値を昇順に並べることができない．
- よって，小さな値から順番に左に swap していき，swap した場所を flag として保管しておく．
- 1 回しか swap することができないので，swap した場所の flag が立っていたら即終了．
- そうでないならば，今見ている値を順番に行けるところまで swap させていく．
	- その際には，position が持っている値を入れ替えて，p の値も入れ替える．

## Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> p(n), pos(n), res;
	REP(i, n) cin >> p[i], pos[--p[i]] = i;

	vector<bool> used(n-1, false);
	REP(i, n) {
		int now = pos[i];
		while (i < now) {
			int before = now - 1;
			if (used[before]) { cout << -1 << '\n'; return 0; }
			used[before] = true;
			pos[p[now]] = before;
			pos[p[before]] = now;
			swap(p[before], p[now]);
			res.emplace_back(before);
			now--;
		}
	}

	if ((int)res.size() != n-1) cout << -1 << '\n';
	else REP(i, n-1) cout << res[i] + 1 << '\n';
    return 0;
}
```