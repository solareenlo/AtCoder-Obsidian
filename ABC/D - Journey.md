# D - Journey
[[確率]] [[Graph]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#確率 #Graph #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc194/tasks/abc194_d

## 解き方
- [競技プログラミングにおける確率・期待値問題 - はまやんはまやんはまやん](https://blog.hamayanhamayan.com/entry/2016/11/14/223727)
  - 「有効なのが来るまでカードを引く期待値は、有効なカードを引く確率の逆数になる。」
-  https://blog.hamayanhamayan.com/entry/2021/03/07/000733

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	res := 0.0
	for i := 1; i < n; i++ {
		res += 1.0 / float64(i)
	}

	fmt.Println(res * float64(n))
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int	n; cin >> n;
	double res = 0.0;
	for (int i=1; i<n; i++)
		res += 1.0*n/(n-i);
	printf("%.10f\n", res);
    return 0;
}
```