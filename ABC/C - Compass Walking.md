# C - Compass Walking
[[グリッド]] [[ユークリッド距離]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#グリッド #ユークリッド距離 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc198/tasks/abc198_c

## 解き方
### Code Go
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var r, x, y float64
	fmt.Scan(&r, &x, &y)

	d := math.Sqrt(x*x + y*y)
	if d < r {
		fmt.Println(2)
	} else {
		fmt.Println(math.Ceil(d / r))
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string n; cin >> n;
	while (n.back() == '0')
		n.pop_back();
	string m = n;
	reverse(m.begin(), m.end());
	cout << (n==m?"Yes":"No") << '\n';
	return 0;
}
```