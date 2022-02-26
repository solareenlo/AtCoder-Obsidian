# B - Products of Min-Max
[[MOD]] [[ACL]] [[min-max]] [[数学的考察]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#MOD #ACL #min-max #数学的考察 #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc116/tasks/arc116_b

## 解き方
- https://atcoder.jp/contests/arc116/editorial/891

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

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)

	const mod = 998244353
	res := 0
	pre := 0
	for i := 0; i < n; i++ {
		res += ((pre + a[i]) % mod) * a[i] % mod
		res %= mod
		pre = (pre*2%mod + a[i]) % mod
	}
	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using mint=atcoder::modint998244353;

int main() {
	int n; cin >> n;
	int a[n];
	for (auto &x : a) cin >> x;
	sort(a, a+n);
	mint res=0, pre=0;
	for (int i=0; i<n; i++) {
		res+=(pre+a[i])*a[i];
		pre=pre*2+a[i];
	}
	cout << res.val() << '\n';
	return 0;
}
```