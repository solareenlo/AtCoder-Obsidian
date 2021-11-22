# E - Unique Color
[[DFS]] [[Tree]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#DFS #Tree #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc198/tasks/abc198_e

## 解き方
- https://blog.hamayanhamayan.com/entry/2021/04/11/225651

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var (
	c   = [100010]int{}
	s   = [100010]int{}
	res = [100010]int{}
	e   = make([][]int, 100010)
)

func dfs(u, p int) {
	if s[c[u]] == 0 {
		res[u] = 1
	}
	s[c[u]]++
	for _, x := range e[u] {
		if x != p {
			dfs(x, u)
		}
	}
	s[c[u]]--
}

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n int
	fmt.Fscan(in, &n)

	for i := 1; i < n+1; i++ {
		fmt.Fscan(in, &c[i])
	}

	for i := 1; i < n; i++ {
		var a, b int
		fmt.Fscan(in, &a, &b)
		e[a] = append(e[a], b)
		e[b] = append(e[b], a)
	}

	dfs(1, 0)

	for i := 1; i < n+1; i++ {
		if res[i] != 0 {
			fmt.Fprintln(out, i)
		}
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=1; i<(n); i++)
using namespace std;

int c[100010], s[100010], res[100010];
vector<int> e[100010];

void dfs(int u, int p) {
	if (s[c[u]] == 0)
		res[u] = 1;
	s[c[u]]++;
	for (int x : e[u]) if (x!=p)
		dfs(x, u);
	s[c[u]]--;
}

int main() {
	int n; cin >> n;
	REP(i, n+1) cin >> c[i];
	REP(i, n) {
		int a, b; cin >> a >> b;
		e[a].push_back(b);
		e[b].push_back(a);
	}
	dfs(1, 0);
	REP(i, n+1) if (res[i])
		cout << i << '\n';
	return 0;
}
```