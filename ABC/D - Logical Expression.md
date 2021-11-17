# D - Logical Expression
[[AND]] [[論理和]] [[OR]] [[論理積]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#AND #論理和 #OR #論理積 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc189/tasks/abc189_d

## 解き方
- $S_1,\ ...,\ S_N$ に対する答えを $f(S_1,\ ...,\ S_N)$ とする．
-  $S_N$ が `AND` のとき，$y_{N−1}$ と $x_N$ はともに True でなければならない．
	- よって $f(S_1,\ ...,\ S_N)=f(S_1,\ ...,\ S_{N−1})$．
-  $S_N$ が`OR` のとき，$x_N$ が True なら $y_{N−1}$ は何でもよく，$x_N$ が False なら $y_{N−1}$ は True でなければならない．
	- よって $f(S_1,\ ...,\ S_N)=2^N+f(S_1,\ ...,\ S_{N−1})$．
- よって，この問題は時間計算量 $O(N)$ で解ける．	
- 以上のことを発見できるかどうかが鍵となる．

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res, x := 1, 1
	for i := 0; i < n; i++ {
		x <<= 1
		var s string
		fmt.Scan(&s)
		if s == "OR" {
			res += x
		}
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
	int64_t res = 1, x = 1;
	while (n--) {
		x <<= 1;
		string s; cin >> s;
		if (s == "OR") res += x;
	}
	cout << res << '\n';
    return 0;
}
```