# C - To Infinity
[[文字列]] [[文字列操作]] [[パターン]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#文字列 #文字列操作 #パターン #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc106/tasks/abc106_c

## 解き方
- $5000$ 兆回繰り返すので，$k$ までに出現する初めての $2$ 以上の数が答えとなる．
- $1$ から $k$ まで全てが $1$ ならば，答えは $1$ になる．

### Code Go
```go
package main

import "fmt"

func main() {
	var s string
	var k int
	fmt.Scan(&s, &k)

	for i := 0; i < min(len(s), k); i++ {
		if s[i] > '1' {
			fmt.Println(string(s[i]))
			return
		}
	}
	fmt.Println(1)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s; cin >> s;
	int64_t k; cin >> k;
	for (int i = 0; i < min(int64_t(s.size()), k); i++)
		if (s[i] > '1') {
			cout << s[i] << '\n';
			return 0;
		}
	cout << 1 << '\n';
	return 0;
}
```