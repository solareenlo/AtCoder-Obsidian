# B - 直線塗り
[[パターン]] [[グリッド]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#パターン #グリッド #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc040/tasks/arc040_b


## 解き方
- パターン発見
- 逆から考える
- 基本的には，一番近い色が塗られていない場所がギリギリ届くところまで移動して行って，インクを発射して色を塗る．
- 最後だけ，一番後ろの色が塗られていない場所がギリギリ届くところまで移動して行って，インクを発射して色を塗る．
- 色を塗ると `.` を `o` に変換する．
- この作業を繰り返した数をカウントすれば良い．
- 逆から考えると短く実装できる．


## Code Go
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var n, r int
	var s string
	fmt.Scan(&n, &r, &s)
	s += strings.Repeat(" ", r)

	cnt := 0
	for i := 0; i < n; i++ {
		target := false
		for j := i; j < i+r; j++ {
			if s[j] == '.' {
				target = true
			}
		}
		if target {
			for j := i; j < i+r; j++ {
				if j < n {
					tmp := strings.Split(s, "")
					tmp[j] = "o"
					s = strings.Join(tmp, "")
				}
			}
			cnt++
		}
		point := 0
		for j := i; j < n; j++ {
			if s[j] == '.' {
				for k := j; k < j+r; k++ {
					if s[k] == '.' {
						point = k
					}
				}
				if point != 0 {
					point -= r - 1
				}
				break
			}
		}
		if point > i {
			cnt += point - i
			i = point - 1
		}
	}

	fmt.Println(cnt)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, r; cin >> n >> r;
	string s; cin >> s;
	reverse(s.begin(), s.end());

	int cnt = 0;
	REP(i, n) {
		if (s[i] == 'o') continue ;
		if (cnt == 0) // 最後のところだけレンジが届くところまで1回で色を塗る
			cnt = max(0, (n - 1) - (i + r - 1));
		cnt++; // 最後以外は1個ずつカウントを増やす
		for (int j = i; j < i + r; j++)
			if (j < n)
				s[j] = 'o';
	}
	cout << cnt << '\n';
	return 0;
}
```
