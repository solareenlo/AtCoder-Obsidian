# C - 2D Plane 2N Points
[[パターン]] [[グリッド]] [[座標]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#パターン #グリッド #座標 #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc092/tasks/arc092_a


## 解き方
- 青い点より $x,\ y$ 座標が小さく，まだ仲良しペアになっていない赤い点を探す．
-  なかったらなにもしない．
- あったら，その中で最もy座標が大きいものを探し，仲良しペアにする．

というアルゴリズムで最適解が求まる．

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	red := make([]P, n)
	blue := make([]P, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &red[i].x, &red[i].y)
	}
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &blue[i].x, &blue[i].y)
	}
	sort.Slice(blue, func(i, j int) bool {
		return blue[i].x < blue[j].x
	})

	res := 0
	for i := 0; i < n; i++ {
		hit := P{-1, -1}
		var index int
		for j := 0; j < len(red); j++ {
			if red[j].x < blue[i].x && red[j].y < blue[i].y && hit.y < red[j].y {
				hit = red[j]
				index = j
			}
		}
		if hit.x != -1 && hit.y != -1 {
			res++
			red = erase(red, index)
		}
	}
	fmt.Println(res)
}

type P struct{ x, y int }

func erase(a []P, pos int) []P {
	return append(a[:pos], a[pos+1:]...)
}
```
### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using P = pair<int, int>;

int main() {
	int n; cin >> n;
	vector<P> red(n), blue(n);
	REP(i, n) cin >> red[i].first >> red[i].second;
	REP(i, n) cin >> blue[i].first >> blue[i].second;
	sort(blue.begin(), blue.end());

	int res = 0;
	REP(i, n) {
		P hit = {-1, -1};
		int index;
		REP(j, (int)red.size()) {
			if (red[j].first < blue[i].first
					&& red[j].second < blue[i].second
					&& hit.second < red[j].second) {
				hit = red[j];
				index = j;
			}
		}
		if (hit != make_pair(-1, -1)) {
			res++;
			red.erase(red.begin() + index);
		}
	}
	cout << res << '\n';
    return 0;
}
```