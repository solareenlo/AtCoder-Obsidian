# C - Unexpressed
[[数学的考察]] [[全探索]] [[Gray]] [[ABC]] [[Go]] [[CPP]]
#数学的考察 #全探索 #Gray #ABC  #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc193/tasks/abc193_c

## 解き方
- $a^b$ と表せる数が少ないので，$a^b<N$ となる $(a,\ b)$ の組合せを set を用いて全探索する．

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	m := map[int]struct{}{}
	for i := 2; i*i < n+1; i++ {
		for j := i * i; j < n+1; j *= i {
			m[j] = struct{}{}
		}
	}

	fmt.Println(n - len(m))
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
  int64_t n; cin >> n;
  set<int64_t> s;
  for (int64_t i=2; i*i<=n; i++)
    for (int64_t j=i*i; j<=n; j*=i)
      s.insert(j);
  cout << n-(int64_t)s.size() << '\n';
  return 0;
}
```