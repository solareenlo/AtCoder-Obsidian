# C - Snukeと対戦！
[[グリッド]] [[パターン]] [[Black]] [[Others]]
#グリッド #パターン #Black #Others 

## 問題
- https://atcoder.jp/contests/gwcontest2015/tasks/gw2015_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int h, w; cin >> h >> w;
	if (h%2 && w%2)
		printf("First\n%d %d %d\n", h/2+1, w/2+1, 1);
	else
		printf("Second\n");
	int a, b, c;
	while (cin >> a >> b >> c, a!=-1)
		printf("%d %d %d\n", h-a+1, w-b+1, ((h%2&&w%2)?c:c^1));
	return 0;
}
```