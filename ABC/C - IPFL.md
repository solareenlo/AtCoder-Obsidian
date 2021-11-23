# C - IPFL
[[文字列操作]] [[文字列]] [[swap]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#文字列操作 #文字列 #swap #Brown #ABC #Go #CPP

## 問題
- https://atcoder.jp/contests/abc199/tasks/abc199_c

## 解き方
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
	var n, q int
	var s []byte
	fmt.Scan(&n, &s, &q)
	flip := false
	for i := 0; i < q; i++ {
		var t, a, b int
		fmt.Fscan(in, &t, &a, &b)
		a--
		b--
		if t == 1 {
			if flip {
				a, b = (a+n)%(n*2), (b+n)%(n*2)
			}
			s[a], s[b] = s[b], s[a]
		} else {
			flip = !flip
		}
	}
	if flip {
		fmt.Println(string(s[n:]) + string(s[:n]))
	} else {
		fmt.Println(string(s))
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	int q; cin >> q;
	bool flip = false;
	while (q--) {
		int t, a, b; cin >> t >> a >> b;
		if (t == 1)
			swap(s[(--a+n*flip)%(n*2)], s[(--b+n*flip)%(n*2)]);
		else
			flip = !flip;
	}
	cout << (flip? s.substr(n) + s.substr(0, n):s) << '\n';
	return 0;
}
```