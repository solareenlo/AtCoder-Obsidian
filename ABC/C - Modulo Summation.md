# C - Modulo Summation
[[MOD]] [[数学的考察]] [[Gray]] [[ABC]] [[Go]] [[CPP]]
#MOD #数学的考察 #Gray #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc103/tasks/abc103_c

## 解き方
- $m=a_1×a_2\times \cdots \times a_N$ とすると，
	- 各 $i$ について $m \mod a_i =0$ なので，
	- 各 $i$ について $(m−1)\mod a_i = a_i−1$．
- したがって $f(m − 1) = (a_1 − 1) + (a_2 − 1) \times \cdots \times (a_n − 1)$ となり，各項が最大値を取っているのでこれが $f$ の最大値となる．

### Code Go
```go
package main

import "fmt"

func main() {
	var n, a, sum int
	fmt.Scan(&n)
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		sum += a - 1
	}
	fmt.Println(sum)
}
```

### Code Go
```c++
#include<bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int res = 0;
	while (n--) {
		int a; cin >> a;
		res += a - 1;
	}
	cout << res << '\n';
}
```