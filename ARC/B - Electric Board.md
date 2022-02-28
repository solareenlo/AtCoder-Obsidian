# B - Electric Board
[[パターン]] [[上界]] [[下界]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#パターン #上界 #下界 #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc119/tasks/arc119_b

## 解き方
- https://atcoder.jp/contests/arc119/editorial/1841

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	var s, t string
	fmt.Fscan(in, &n, &s, &t)

	a := make([]int, 0)
	b := make([]int, 0)
	for i := 0; i < n; i++ {
		if s[i] == '0' {
			a = append(a, i)
		}
		if t[i] == '0' {
			b = append(b, i)
		}
	}

	res := 0
	for i := 0; i < len(a); i++ {
		if a[i] != b[i] {
			res++
		}
	}
	if len(a) != len(b) {
		res = -1
	}
	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	string s, t; cin >> s >> t;
	vector<int> a, b;
	REP(i, n) {
		if (s[i] == '0') a.push_back(i);
		if (t[i] == '0') b.push_back(i);
	}
	int res = 0;
	REP(i, (int)a.size())
		if (a[i] != b[i])
			res++;
	if ((int)a.size() != (int)b.size())
		res = -1;
	cout << res << '\n';
    return 0;
}
```