# C - ℕ Coloring
[[素因数]] [[builtin]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#素因数 #builtin #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc115/tasks/arc115_c

## 解き方
### Code 素因数の個数 Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	for i := 1; i <= n; i++ {
		cnt := 1
		a := i
		for j := 2; j*j <= i; j++ {
			for a%j == 0 {
				a /= j
				cnt++
			}
		}
		if a > 1 {
			cnt++
		}
		fmt.Print(cnt, " ")
	}
	fmt.Println()
}
```

### Code 素因数の個数 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	for (int i=1; i<=n; i++) {
		int cnt=1;
		int a=i;
		for (int j=2; j*j<=i; j++)
			while (a%j==0)
				a/=j, cnt++;
		if (a>1) cnt++;
		cout << cnt << " ";
	}
	return 0;
}
```

### Code log2 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	for (int i=1; i<=n; i++)
		cout << int(log2(i))+1 << " ";
    return 0;
}
```

### Code __builtin_clz CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	for (int i=1; i<=n; i++)
		cout << 32-__builtin_clz(i) << " ";
	return 0;
}
```