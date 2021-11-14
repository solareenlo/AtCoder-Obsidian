# C - Green Bin
[[文字列]] [[文字列操作]] [[sort]] [[個数]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#文字列 #文字列操作 #sort #個数 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc137/tasks/abc137_c

## 解き方
- それ以降に同じ文字を使った文字列が何個あるのかを探索するので，
- 言い換えるとそれまでに同じ文字を使った文字列が何個あるのかを数え，足し合わせたものが答えになる．

### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)

	str := map[string]int{}
	res := 0
	for i := 0; i < n; i++ {
		var s string
		fmt.Scan(&s)
		b := make([]byte, len(s))
		for i := range s {
			b[i] = s[i]
		}
		sort.Slice(b, func(i, j int) bool {
			return b[i] < b[j]
		})
		res += str[string(b)]
		str[string(b)]++
	}
	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	map<string, int> str;
	int64_t res = 0;
	while (n--) {
		string s; cin >> s;
		sort(s.begin(), s.end());
		res += str[s]++;
	}
	cout << res << '\n';
	return 0;
}
```