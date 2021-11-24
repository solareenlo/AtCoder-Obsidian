# C - Ringo's Favorite Numbers 2
[[数学的考察]] [[Gray]] [[ABC]] [[Go]] [[CPP]]
#数学的考察 #Gray #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc200/tasks/abc200_c

## 解き方
- 200 で割った余りが同じ数の個数を数え上げる．

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
	var n int
	fmt.Scan(&n)
	s := make([]int64, 200)
	res := int64(0)
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		res += s[a%200]
		s[a%200]++
	}
	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;
int64_t s[200], res;
int main() {
	int n, a; cin >> n;
	while (n--) {
		cin >> a;
		res += s[a%200]++;
	}
	cout << res << '\n';
	return (0);
}
```