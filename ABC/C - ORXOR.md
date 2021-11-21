# C - ORXOR
[[OR]] [[xor]] [[bit全探索]] [[DFS]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#OR #xor #bit全探索 #DFS #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc197/tasks/abc197_c

## 解き方
### Code DFS Go
```go
package main

import "fmt"

var (
	n   int
	a       = [30]int{}
	res int = 1 << 60
)

func dfs(x, s1, s2 int) {
	if x == n {
		res = min(res, s1^s2)
		return
	}
	dfs(x+1, s1|a[x], s2)
	dfs(x+1, a[x], s1^s2)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func main() {
	fmt.Scan(&n)

	for i := 0; i < n; i++ {
		fmt.Scan(&a[i])
	}

	dfs(0, 0, 0)

	fmt.Println(res)
}
```

### Code bit 全探索 CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
int n, a[21], res=2e9;
int main() {
	cin >> n;
	REP(i, n) cin >> a[i];
	REP(bit, 1<<(n-1)) {
		int xored=0, ored=0;
		REP(i, n+1) {
			if (i<n) ored|=a[i];
			if (i==n || bit>>i&1) xored^=ored, ored=0;
		}
		res = min(res, xored);
	}
	cout << res << '\n';
	return 0;
}
```

### Code DFS CPP
```c++
#include <bits/stdc++.h>
using namespace std;
int n, a[30], res=2e9;

void dfs(int x, int s1, int s2) {
	if (x == n) {
		res = min(res, s1^s2);
		return ;
	}
	dfs(x+1, s1|a[x], s2);
	dfs(x+1, a[x], s1^s2);
}

int main() {
	cin >> n;
	for (int i=0; i<n; i++) cin >> a[i];
	dfs(0, 0, 0);
	cout << res << '\n';
    return 0;
}
```