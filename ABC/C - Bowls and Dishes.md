# C - Bowls and Dishes
[[bit全探索]] [[全探索]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#bit全探索 #全探索 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc190/tasks/abc190_c

## 解き方
- $2^k$ 通りのボールを置いた，置いてない，を bit 全探索する．

### Code Go
```Go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	type pair struct{ a, b int }
	ab := make([]pair, m)
	for i := range ab {
		fmt.Scan(&ab[i].a, &ab[i].b)
	}

	var k int
	fmt.Scan(&k)
	cd := make([]pair, k)
	for i := range cd {
		fmt.Scan(&cd[i].a, &cd[i].b)
	}

	res := 0
	for bit := 0; bit < 1<<k; bit++ {
		ball := make([]bool, 101)
		for i := 0; i < k; i++ {
			if bit&(1<<i) != 0 {
				ball[cd[i].a] = true
			} else {
				ball[cd[i].b] = true
			}
		}
		cnt := 0
		for i := range ab {
			if ball[ab[i].a] && ball[ab[i].b] {
				cnt++
			}
		}
		res = max(res, cnt)
	}

	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using P = pair<int, int>;

int main() {
	int n, m; cin >> n >> m;
	P ab[m];
	for (auto &[a, b] : ab) cin >> a >> b;
	int k; cin >> k;
	P cd[k];
	for (auto &[c, d] : cd) cin >> c >> d;

	int res = 0;
	REP(bit, 1<<k) {
		bool ball[100] = {0};
		REP(i, k) {
			auto [c, d] = cd[i];
			ball[bit & 1<<i ? c : d] = 1;
		}
		int cnt = 0;
		for (auto [a, b] : ab) if (ball[a] && ball[b]) cnt++;
		res = max(res, cnt);
	}
	cout << res << '\n';
    return 0;
}
```