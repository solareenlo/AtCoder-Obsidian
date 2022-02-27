# B - ARC Wrecker
[[総積]] [[数え上げ]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#総積 #数え上げ #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc117/tasks/arc117_b

## 解き方
- https://atcoder.jp/contests/arc117/editorial/1111

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}
	tmp := a[1 : n+1]
	sort.Ints(tmp)

	res := 1
	for i := 1; i <= n; i++ {
		res *= (a[i] - a[i-1] + 1)
		res %= 1000000007
	}

	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;
int64_t a[1000001], n, res=1;
int main() {
	cin >> n;
	for (int i=1; i<=n; i++) cin>>a[i];
	sort(a+1, a+n+1);
	for (int i=1; i<=n; i++) (res*=(a[i]-a[i-1]+1))%=1000000007;
	cout<<res<<'\n';
	return 0;
}
```