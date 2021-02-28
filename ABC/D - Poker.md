# D - Poker
[[確率]] [[数学的考察]] [[文字列操作]] [[Green]] [[ABC]]
#確率 #数学的考察 #文字列操作 #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc193/tasks/abc193_d

## 解き方
- https://atcoder.jp/contests/abc193/editorial/810

### Code2
```c++
#include <bits/stdc++.h>
#define int int64_t
using namespace std;
int n, res;

int score(string s) {
  int n[10] = {};
  iota(n, n+10, 0);
  for (char c : s) n[c-'0'] *= 10;
  return accumulate(n, n+10, 0);
}

signed main() {
  string s, t; cin >> n >> s >> t;
  vector<int> cnt(10, n);
  for (char c : s+t) cnt[c-'0']--;
  for (int x=1; x<10; x++) for (int y=1; y<10; y++) {
    s.back() = x+'0';
    t.back() = y+'0';
    if (score(s) <= score(t)) continue;
    res += cnt[x]*(cnt[y]-(x==y));
  }
  cout << double(res)/(9*n-8)/(9*n-9) << '\n';
  return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int n, t1[10], t2[10], sum1, sum2;
string a, b;
double res;
int main() {
  cin >> n >> a >> b;
  REP(i, 4) t1[a[i]-'0']++, t2[b[i]-'0']++;
  REP(i, 10) sum1 += i*pow(10, t1[i]), sum2 += i*pow(10, t2[i]);
  for (int i=1; i<10; i++) for (int j=1; j<10; j++) {
    int A = sum1+9*i*pow(10,t1[i]);
    int T = sum2+9*j*pow(10,t2[j]);
    if (A>T) res += 1.0*(n-t1[i]-t2[i])/(9*n-8)*(n-t1[j]-t2[j]-(i==j))/(9*n-9);
  }
  printf("%.10f\n", res);
  return 0;
}
```