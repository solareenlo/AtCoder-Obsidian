# B - Visibility
[[グリッド]] [[Gray]] [[ABC]]
#グリッド #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc197/tasks/abc197_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int h, w, x, y; cin >> h >> w >> x >> y;
	x--, y--;
	string s[h];
	for (auto &a : s) cin >> a;
	int i, j, res=0;
	i=x, j=y; while (i>=0 && s[i][j]=='.') i--, res++;
	i=x, j=y; while (j>=0 && s[i][j]=='.') j--, res++;
	i=x, j=y; while (i<h && s[i][j]=='.') i++, res++;
	i=x, j=y; while (j<w && s[i][j]=='.') j++, res++;
	cout << res-3 << '\n';
    return 0;
}
```