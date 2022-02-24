# B - -- - B
[[条件分岐]] [[数学的考察]] [[min-max]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#条件分岐 #数学的考察 #min-max #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc112/tasks/arc112_b

## 解き方
- 条件に分けて考える問題．
- $C$ が奇数の場合
  - $C = 2n + 1$ とすると，
  - $-B-n$ 以上 $-B+n$ 以下の整数が作れる．
- $C$ が偶数の場合
  - $C$ が $0$ の時は，$B$ 種類作れる．
  - $C = 2n$ とすると，
  - $B - n$ 以上 $B+n-1$ 以下の整数が作れる．
- https://atcoder.jp/contests/arc112/editorial/725

### Code Go
```go
package main

import "fmt"

func main() {
	var b, c int
	fmt.Scan(&b, &c)

	var res int
	if b == 0 {
		res = c
	} else if c == 0 {
		res = 1
	} else if c >= 2*abs(b) {
		tmp := 0
		if b > 0 {
			tmp = 1
		}
		res = c + 2*abs(b) - tmp
	} else if c == 1 {
		res = 2
	} else {
		res = 2*c - 1
	}
	fmt.Println(res)
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```

### Code1 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

inline pair<long, long> exact(const long b, const long c) {
	const auto n = c / 2;
	if (c % 2) return {-b - n, -b + n};
	else {
		if (c) return {b - n, b + n - 1};
		else return {b, b};
	}
}

int main() {
	long B, C; cin >> B >> C;
	const auto [a, b] = exact(B, C);
	const auto [c, d] = exact(B, C-1);
	cout << (b-a+1)+(d-c+1)-max(0L, min(b,d)-max(a,c)+1) << '\n';
    return 0;
}
```

### Code2 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t b, c; cin >> b >> c;
	int64_t res;
	if (b == 0) res = c;
	else if (c == 0) res = 1;
	else if (c >= 2*llabs(b)) res = c+2*llabs(b)-(b>0);
	else if (c == 1) res = 2;
	else res = 2*c-1;
	cout << res << '\n';
	return 0;
}
```