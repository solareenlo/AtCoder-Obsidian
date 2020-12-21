# B - 赤と黒の木
[[円循環]] [[パターン]] [[Light Blue]] [[ARC]]
#円循環 #パターン #Light_Blue #ARC 

## 問題
- https://atcoder.jp/contests/arc024/tasks/arc024_2

## 解き方
- パターンを考える．
- 隣に異なる色がいる木はそれ以降ずっと変化しない．
	- 連続する同じ色の塊だけを見れば良いということ．
- $X$個連続して同じ色が並ぶと $[(x-1)/2]$ 日後に止まる．
	- ただし $[X]$ は $x$ を超えない最大の整数を表す．
- 円循環だと考えづらいので，どこかで切って，1行にして，それを2つ分繋げた1行で考える．	
- 全部同じ色だった場合は，$-1$ が答えとなる．

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int n, cnt, res, c[200002];
int main() {
	cin >> n;
	REP(i, n) cin >> c[i];
	REP(i, n) c[i+n] = c[i];
	REP(i, 2*n)
		if (c[i] == c[i-1]) res = max(res, ++cnt/2+1);
		else cnt = 0;
	cout << (cnt>n ? -1 : res) << '\n';
	return 0;
}
```

### Code2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> c(2*n, 0);
	REP(i, n) {
		cin >> c[i];
		c[i+n] = c[i];
	}
	int r = 0, now = c[0], res = -1;
	REP(i, 2*n) {
		if (now == c[i]) r++;
		else {
			res = max(res, ((r-1)/2)+1);
			now = c[i];
			r = 1;
		}
	}
	cout << res << '\n';
    return 0;
}
```