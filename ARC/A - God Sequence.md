# A - God Sequence
[[数列]] [[パターン]] [[Gray]] [[ARC]] [[CPP]] [[Go]]
#数列 #パターン #Gray #ARC #CPP #Go

## 問題
- https://atcoder.jp/contests/arc117/tasks/arc117_a

## 解き方
- いくつかの条件を撤廃した「簡単な問題」を考える．
- 数列などの要素を 1 つ変えることで，答えが導けるか考える．

### Code Go
```go
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scan(&a, &b)

	sum := 0
	for i := 1; i < a; i++ {
		fmt.Print(i, " ")
		sum += i
	}
	for i := 1; i < b; i++ {
		fmt.Print(-i, " ")
		sum -= i
	}

	if a > b {
		fmt.Println(a, -sum-a)
	} else if a < b {
		fmt.Println(-b, -sum+b)
	} else {
		fmt.Println(a, -b)
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i < (n); i++)
using namespace std;

int main() {
	int a, b; cin >> a >> b;
	int sum = 0;
	REP(i, a) cout << i << " ", sum+=i;
	REP(i, b) cout << -i << " ", sum-=i;
	if (a>b) cout << a << " " << -sum-a;
	else if (a<b) cout << -b << " " << -sum+b;
	else cout << a << " " << -b;
    return 0;
}
```