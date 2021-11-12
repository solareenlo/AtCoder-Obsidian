# D - Hachi
#Number_theory #Brown #ABC #Go #CPP 
[[Number theory]] [[Brown]] [[ABC]] [[Go]] [[CPP]]

## 問題
- [D - Hachi](https://atcoder.jp/contests/abc181/tasks/abc181_d)

## 解き方
- $8$ の倍数になるときの下 $3$ 桁の候補  $000,\ 008,\ 016,\ \cdots,\ 976,\ 984,\ 992$ がそれぞれ作れるかどうかを調べることで， `O(|S|)` でこの問題を解くことができる．

### Code Go
```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	ok := false

	if n == 1 {
		if s[0] == '8' {
			ok = true
		}
	} else if n == 2 {
		t, _ := strconv.Atoi(s)
		if t%8 == 0 {
			ok = true
		}
		a, b := string(s[0]), string(s[1])
		s = b + a + s[2:]
		t, _ = strconv.Atoi(s)
		if t%8 == 0 {
			ok = true
		}
	} else {
		cnt := make([]int, 10)
		for _, x := range s {
			cnt[x-'0']++
		}
		for i := 112; i < 1000; i += 8 {
			c := make([]int, 10)
			copy(c, cnt)
			for _, x := range strconv.Itoa(i) {
				c[x-'0']--
			}
			tmp := 0
			for j := 0; j < 10; j++ {
				if c[j] >= 0 {
					tmp++
				}
			}
			if tmp == 10 {
				ok = true
			}
		}
	}

	if ok {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}
}
```

## Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s; cin >> s;
	int n = s.size();
	bool ok = false;
	if (n == 1) {
		if (s[0] == '8')
			ok = true;
	}
	else if (n == 2) {
		if (stoi(s) % 8 == 0)
			ok = true;
		swap(s[0], s[1]);
		if (stoi(s) % 8 == 0)
			ok = true;
	}
	else {
		vector<int> cnt(10, 0);
		for (auto x : s)
			cnt[x - '0']++;
		for (int i = 112; i < 1000; i += 8) {
			auto c = cnt;
			for (char x : to_string(i))
				c[x - '0']--;
			int tmp = 0;
			for (int i = 0; i < 10; i++)
				if (c[i] >= 0)
					tmp++;
			if (tmp == 10)
				ok = true;
		}
	}
	cout << (ok ? "Yes" : "No") << '\n';
	return 0;
}
```