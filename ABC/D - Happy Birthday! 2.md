# D - Happy Birthday! 2
[[鳩ノ巣原理]] [[bit全探索]] [[DFS]] [[Light Blue]] [[ABC]] [[Go]] [[CPP]]
#鳩ノ巣原理 #bit全探索 #DFS #Light_Blue #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc200/tasks/abc200_d

## 解き方
- https://atcoder.jp/contests/abc200/editorial/1246

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	b := make([][]int, 200)
	for i := range b {
		b[i] = make([]int, 0)
	}

	cnt := min(n, 8)
	for bit := 1; bit < 1<<cnt; bit++ {
		sig := 0
		s := make([]int, 0)
		for i := 0; i < cnt; i++ {
			if bit&(1<<i) > 0 {
				s = append(s, i+1)
				sig += a[i]
				sig %= 200
			}
		}
		if len(b[sig]) != 0 {
			fmt.Println("Yes")
			output(b[sig])
			output(s)
			return
		} else {
			b[sig] = s
		}
	}
	fmt.Println("No")
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func output(a []int) {
	fmt.Print(len(a))
	for _, x := range a {
		fmt.Print(" ", x)
	}
	fmt.Println()
}
```

### Code bit 全探索 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

void output(vector<int> &a) {
	cout << a.size();
	for (int &x : a)
		cout << " " << x;
	cout << "\n";
}

int main() {
	int n; cin >> n;
	vector<int> a(n);
	for (int &x : a) cin >> x;
	vector<int> b[200];
	int cnt = min(n, 8);
	for (int bit=1; bit<(1<<cnt); bit++) {
		int sig = 0;
		vector<int> s;
		for (int i=0; i<cnt; i++) if (bit&(1<<i)) {
			s.push_back(i+1);
			(sig += a[i]) %= 200;
		}
		if (b[sig].size() != 0) {
			cout << "Yes" << '\n';
			output(b[sig]);
			output(s);
			return (0);
		}
		else
			b[sig] = s;
	}
	cout << "No" << '\n';
    return 0;
}
```