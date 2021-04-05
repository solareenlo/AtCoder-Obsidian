# B - アリ巣
[[パターン]] [[グリッド]] [[Black]] [[Others]]
#パターン #グリッド #Black #Others 

## 問題
- https://atcoder.jp/contests/gwcontest2015/tasks/gw2015_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

const int dx[4] = {0,1,0,-1};
const int dy[4] = {1,0,-1,0};
int x, y, st, v[2000][2000];

/*
ある程度シミュレーションすると周期的な構造が見つかる
11500stepくらいから先はずっと周期的に移動し続ける
*/

int main() {
	int64_t n; cin >> n;
	if (n >= 10000)
		n = 10000+(n-10000)%104;
	x = y = 1000;
	while (n--) {
		st = (v[y][x] ? (st+1)%4 : (st+3)%4);
		v[y][x] = 1 - v[y][x];
		x += dx[st];
		y += dy[st];
	}
	cout << v[y][x] << '\n';
	return 0;
}
```