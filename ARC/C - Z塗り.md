# C - Z塗り
[[パターン]] [[グリッド]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#パターン #グリッド #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc040/tasks/arc040_c

## 解き方
- まだ塗られていないマスのうち右上のものを探す ． 
- そのマスにZ字の右上の⾓角を合わせるように塗る．
-  以上を繰り返し，全部のマスが塗られるまでに繰り返した回数が答えとなる．

### Code GO
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	s := make([]string, n+1)
	for i := 0; i < n; i++ {
		fmt.Scan(&s[i])
	}

	res := 0
	for i := 0; i < n; i++ {
		pos := -1
		for j := 0; j < n; j++ {
			if s[i][j] == '.' {
				pos = j
			}
		}
		if pos == -1 {
			continue
		}
		for j := 0; j < pos+1; j++ {
			s[i] = replaceAtIndex(s[i], 'o', j)
		}
		for j := pos; j < n && i < n-1; j++ {
			s[i+1] = replaceAtIndex(s[i+1], 'o', j)
		}
		res++
	}

	fmt.Println(res)
}

func replaceAtIndex(in string, r rune, i int) string {
	out := []rune(in)
	out[i] = r
	return string(out)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	char s[n+1][n];
	REP(i, n) REP(j, n) cin >> s[i][j];

	int res = 0;
	REP(i, n) {
		int pos = -1;
		REP(j, n) if (s[i][j] == '.') pos = j;
		if (pos == -1) continue ;
		REP(j, pos+1) s[i][j] = 'o';
		for (int j = pos; j < n; j++) s[i+1][j] = 'o';
		res++;
	}
	cout << res << '\n';
	return 0;
}
```