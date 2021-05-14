# C - Coprime Set
[[数学的考察]] [[GCD]] [[Green]] [[ARC]]
#数学的考察 #GCD #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc118/tasks/arc118_c

## 解き方
- https://atcoder.jp/contests/arc118/editorial/1206

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> res = {6, 10, 15};
	for (int i=16; (int)res.size()<n; i++)
		if (i%6==0 || i%10==0 || i%15==0)
			res.push_back(i);
	for (int x : res)
		cout << x << " ";
	return 0;
}
```