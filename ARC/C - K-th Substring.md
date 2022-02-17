# C - K-th Substring
[[文字列操作]] [[unique]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#文字列操作 #unique #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc097/tasks/arc097_a

## 解き方
- 全ての $s$ の $k$ 文字までの substring を列挙し，重複を除き sort する．
- これは C++ だと sort した後 unique 関数が使える．
- 列挙する必要がある長さ $k$ 以下の substring は $O(NK)$ だけとなり，これをソートすると時間計算量は $O(NK^2(\log NK))$ となり，十分高速である．

### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var s string
	var k int
	fmt.Scan(&s, &k)

	subMap := map[string]struct{}{}
	for i := 0; i < len(s); i++ {
		for j := i + 1; j <= i+k && j <= len(s); j++ {
			subMap[s[i:j]] = struct{}{}
		}
	}

	sub := make([]string, len(subMap))
	i := 0
	for key, _ := range subMap {
		sub[i] = key
		i++
	}
	sort.Strings(sub)

	i = 1
	for x := range sub {
		if i == k {
			fmt.Println(sub[x])
			return
		}
		i++
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	string s; cin >> s;
	int n = s.size();
	int k; cin >> k;
	vector<string> t;
	REP(i, n) REP(j, k)
		if (i + j < n)
			t.push_back(s.substr(i, j+1));
	sort(t.begin(), t.end());
	unique(t.begin(), t.end());
	cout << t[k-1] << '\n';
    return 0;
}
```