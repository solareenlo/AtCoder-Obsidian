# E - Sequence Decomposing
[[数学的考察]] [[広義短調減少]] [[upper_bound]] [[lower_bound]] [[Light Blue]] [[ABC]] [[Go]] [[CPP]]
#数学的考察 #広義短調減少 #upper_bound #lower_bound #Light_Blue #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc134/tasks/abc134_e

## 解き方
- 与えられた数列の，広義単調減少列の長さの最大値が答え．
- ので，与えられた数列から広義短調減少列を作成する問題．
- 証明: https://img.atcoder.jp/abc134/editorial.pdf

### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)

	dp := make([]int, n)
	for i := range dp {
		dp[i] = 10
	}

	for i := 0; i < n; i++ {
		var a int
		fmt.Scan(&a)
		index := sort.SearchInts(dp, -a+1)
		dp[index] = -a
	}

	fmt.Println(sort.SearchInts(dp, 1))
}
```

### Code2 CPP
短いバージョン
```c++
#include <bits/stdc++.h>
using namespace std;
int main() {
	int n; cin >> n;
	int dp[n];
	fill(dp, dp+n, 10);
	for (int i = 0; i < n; i++) {
		int a; cin >> a;
		*upper_bound(dp, dp+n, -a) = -a;
	}
	cout << lower_bound(dp, dp+n, 1) - dp << '\n';
}
```

### Code1 CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n];
	REP(i, n) cin >> a[i];
	cout << '\n';
	vector<int> res;
	REP(i, n) {
		auto itr = lower_bound(res.rbegin(), res.rend(), a[i]);
		if (itr == res.rbegin()) res.push_back(a[i]);
		else {
			--itr;
			*itr = a[i];
		}
	}
	cout << res.size() << '\n';
    return 0;
}
```