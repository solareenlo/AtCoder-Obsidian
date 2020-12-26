# D - 一刀両断
[[面積]] [[符号付き面積]] [[2直線の交点]] [[外積]] [[Light Blue]] [[ABC]]
#面積 #符号付き面積 #2直線の交点 #外積 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc016/tasks/abc016_4

## 解き方
- 分割された多角形の数
- = 切っている線分の本数 + 1
- = 多角形と線分の交点の数 / 2 + 1
- = 線分と交差する多角形の辺の本数 / 2 + 1
- 線分の交差判定には符号付き面積を使う
- 符号付き面積の公式
	- 座標平面上に $3$ 点 $A(a,b),\ B(c,d),\ C(e,f)$ が与えられたとき
	- $(ad+cf+eb-bc-de-fa)/2$ 
	- を三角形 $ABC$ の**符号付面積**という．
	
### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int ax, ay, bx, by; cin >> ax >> ay >> bx >> by;
	int n; cin >> n;
	int x[n], y[n];
	REP(i, n) cin >> x[i] >> y[i];
	int cnt = 0;
	REP(i, n) {
		int cx = x[i];
		int cy = y[i];
		int dx = x[(i+1)%n];
		int dy = y[(i+1)%n];
		int64_t area1 = ax*by + bx*cy + cx*ay - ay*bx - by*cx - cy*ax;
		int64_t area2 = ax*by + bx*dy + dx*ay - ay*bx - by*dx - dy*ax;
		int64_t area3 = cx*dy + dx*ay + ax*cy - cy*dx - dy*ax - ay*cx;
		int64_t area4 = cx*dy + dx*by + bx*cy - cy*dx - dy*bx - by*cx;
		if (area1*area2 < 0 && area3*area4 < 0) cnt++;
	}
	cout << cnt/2+1 << '\n';
	return 0;
}
```

### Code2
- または外積を用いた交差判定を行う．
- http://digilog.usamimi.info/upload/?mode=download&eid=76
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int ax, ay, bx, by; cin >> ax >> ay >> bx >> by;
	int n; cin >> n;
	int x[n], y[n];
	REP(i, n) cin >> x[i] >> y[i];
	int cnt = 0;
	REP(i, n) {
		int cx = x[i];
		int cy = y[i];
		int dx = x[(i+1)%n];
		int dy = y[(i+1)%n];
		int64_t v1 = (ay-by)*cx - (ax-bx)*cy + ax*by - bx*ay;
		int64_t v2 = (ay-by)*dx - (ax-bx)*dy + ax*by - bx*ay;
		int64_t u1 = (cy-dy)*ax - (cx-dx)*ay + cx*dy - dx*cy;
		int64_t u2 = (cy-dy)*bx - (cx-dx)*by + cx*dy - dx*cy;
		if (v1*v2<0 && u1*u2<0) cnt++;
	}
	cout << cnt/2+1 << '\n';
	return 0;
}
```