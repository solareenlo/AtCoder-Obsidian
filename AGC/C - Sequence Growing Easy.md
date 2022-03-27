# C - Sequence Growing Easy
[[パターン]] [[数列]] [[Light Blue]] [[AGC]] [[CPP]] [[Go]]
#パターン #数列 #Light_Blue #AGC #CPP #Go 

## 問題
- https://atcoder.jp/contests/agc024/tasks/agc024_c

## 解き方
- $A_1 > 0$ と $A_{i+1} - A_i > 1$ の場合は，答えは $-1$．
- $A_i = t$ とする．この時，操作によって $X_i$ に $t$ が代入されるためには，$t=0$ であるか，または，$X_{i-1} = t-1$ であるようなタイミングが必要．
- この議論を繰り返し行うことで，$1\leq s\leq t$ に対し，$X_{i-t+s}$ に $s$ が代入されるタイミングが必要となることがわかる．
- この値は，$X_{i-1}+1=X_i$ なら答えに $+1$，そうでないならば答えに $+X_i$ することで求めることができる．

### Code Go2
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
	fmt.Fscan(in, &n)

	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}

	ok := 1
	if a[1] > 0 {
		ok = 0
	}

	ans := 0
	for i := 1; i <= n; i++ {
		if a[i]-a[i-1] > 1 {
			ok = 0
		} else if a[i] == a[i-1]+1 {
			ans += 1
		} else {
			ans += a[i]
		}
	}

	if ok == 0 {
		fmt.Println(-1)
	} else {
		fmt.Println(ans)
	}
}
```

### Code Go1
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
	fmt.Fscan(in, &n)

	res := -1
	now := -1
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		if a > now+1 {
			fmt.Println(-1)
			return
		}
		if a > now {
			res++
		} else {
			res += a
		}
		now = a
	}

	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;
int a[200002];
int main() {
	int n; cin >> n;
	for (int i = 1; i <= n; i++) cin >> a[i];
	int64_t res = -1;
	a[0] = -1;
	if (a[1] > 0) { cout << -1 << '\n'; return 0; }
	for (int i = 1; i <= n; i++) {
		if (a[i+1]-a[i]>1) { cout << -1 << '\n'; return 0; }
		res += (a[i-1]+1==a[i])?1:a[i];
	}
	cout << res << '\n';
	return 0;
}
```