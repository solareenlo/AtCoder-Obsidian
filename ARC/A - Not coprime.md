# A - Not coprime
[[bit全探索]] [[GCD]] [[DFS]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#bit全探索 #GCD #DFS #Brown #ARC  #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc114/tasks/arc114_a

## 解き方
### Code bit 全探索 CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int64_t prime[] = {2,3,5,7,11,13,17,19,23,29,31,37,41,43,47};
int main() {
	int n; cin >> n;
	int64_t x[n];
	REP(i, n) cin >> x[i];
	int64_t res = 1e18;
	REP(bit, 1<<15) {
		int64_t p = 1;
		REP(i, 15) if ((bit>>i)&1) p *= prime[i];
		for (auto a : x) if (gcd(a, p) == 1) goto next;
		res = min(res, p);
next:;
	}
	cout << res << '\n';
	return 0;
}
```

### Code DFS Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var (
	n     int
	x         = [55]int{}
	res   int = 1 << 60
	prime     = []int{2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47}
)

func dfs(i, j int) {
	if i == 15 {
		for i := 0; i < n; i++ {
			if gcd(j, x[i]) == 1 {
				return
			}
		}
		res = min(res, j)
		return
	}
	dfs(i+1, j)
	dfs(i+1, j*prime[i])
}

func main() {
	in := bufio.NewReader(os.Stdin)

	fmt.Fscan(in, &n)

	for i := 0; i < n; i++ {
		fmt.Fscan(in, &x[i])
	}

	dfs(0, 1)

	fmt.Println(res)
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code DFS CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

const int64_t prime[] = {2,3,5,7,11,13,17,19,23,29,31,37,41,43,47};
int n, x[55];
int64_t res = 1e18;

void dfs(int i, int64_t j) {
	if (i == 15) {
		REP(i, n) if (gcd(j, x[i]) == 1) return ;
		res = min(res, j);
		return ;
	}
	dfs(i+1, j);
	dfs(i+1, j*prime[i]);
}

int main() {
	cin >> n;
	REP(i, n) cin >> x[i];
	dfs(0, 1);
	cout << res << '\n';
	return 0;
}
```