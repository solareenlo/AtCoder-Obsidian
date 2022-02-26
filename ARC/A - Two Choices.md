# A - Two Choices
[[パターン]] [[文字列操作]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#パターン #文字列操作 #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc115/tasks/arc115_a

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

	var n, m int
	fmt.Fscan(in, &n, &m)

	res := 0
	for i := 0; i < n; i++ {
		var s string
		fmt.Fscan(in, &s)
		cnt := 0
		for _, c := range s {
			if c == '1' {
				cnt++
			}
		}
		if cnt%2 != 0 {
			res++
		}
	}

	fmt.Println(res * (n - res))
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int64_t res = 0;
	for (int i=0; i<n; i++) {
		string s; cin >> s;
		int cnt = 0;
		for (char c : s) if (c=='1') cnt++;
		if (cnt%2) res++;
	}
	cout << res*(n-res) << '\n';
    return 0;
}
```