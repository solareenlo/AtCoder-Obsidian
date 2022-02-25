# A - A\*B\*C
[[全探索]] [[Gray]] [[ARC]] [[CPP]] [[Go]]
#全探索 #Gray #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc113/tasks/arc113_a

## 解き方
- $A$ を固定した時の，$B$ の候補数は，$K/A$ 個．
- $A,\ B$ を固定した時の，$C$ の候補数は，$K/A/B$ 個．

### Code Go
```go
package main

import "fmt"

func main() {
	var k int
	fmt.Scan(&k)

	res := 0
	for i := 1; i <= k; i++ {
		for j := 1; j <= k/i; j++ {
			for l := 1; l <= k/i/j; l++ {
				res++
			}
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
	int k; cin >> k;
	int res = 0;
	for (int i=1; i<=k; i++)
		for (int j=1; j<=k/i; j++)
			for (int l=1; l<=k/i/j; l++)
				res++;
	cout << res << '\n';
	return 0;
}
```