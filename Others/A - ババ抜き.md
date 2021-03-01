# A - ババ抜き
[[文字列操作]] [[Black]] [[Others]]
#文字列操作 #Black #Others 

## 問題
- https://atcoder.jp/contests/Recruit-Programing-contest-practice/tasks/recruite_2013_pre_a

## 解き方

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
  int t; cin >> t;
  while (t--) {
    int n; cin >> n;
    queue<string> p;
    while (n--) {
      string tmp; cin >> tmp;
      p.push(tmp);
    }
    int cnt = 0;
    for (; p.size()!=1 && cnt<1e6; cnt++) {
      string tmp = p.front(); p.pop();
      char c = p.front()[0];
      p.front().erase(0, 1);
      if (p.front().empty()) p.pop();
      if (tmp.find(c) != -1) tmp.erase(tmp.find(c), 1);
      else tmp += c;
      if (!tmp.empty()) p.push(tmp);
    }
    cout << ((cnt>=1e6) ? -1 : cnt) << '\n';
  }
  return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
  int t; cin >> t;
  while (t--) {
    int n; cin >> n;
    vector<string> a(n);
    for (auto &x : a) cin >> x;
    int res = 0;
    for (; res<1010101 && (int)a.size()>=2; res++) {
      char c = a[1][0];
      a[1].erase(0, 1);
      int p = a[0].find(c);
      if (p != string::npos) a[0].erase(p, 1);
      else a[0].push_back(c);
      bool next = true;
      if (a[1].empty()) a.erase(a.begin()+1);
      if (a[0].empty()) a.erase(a.begin()+0), next = false;
      if (next) rotate(a.begin(), a.begin()+1, a.end());
    }
    cout << ((res==1010101)? -1 : res) << '\n';
  }
  return 0;
}
```