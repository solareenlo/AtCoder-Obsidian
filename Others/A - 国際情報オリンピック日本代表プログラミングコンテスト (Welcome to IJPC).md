# A - 国際情報オリンピック日本代表プログラミングコンテスト (Welcome to IJPC)
[[bit全探索]] [[popcount]] [[Brown]] [[Others]]
#bit全探索 #popcount #Brown #Others 

## 問題
- https://atcoder.jp/contests/ijpc2012pr

## 解き方
- bit 全探索して，その時のビットが立ってる個数の最小値が答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int replace(int N, char S[]) {
	string s = "IJPC";
	int res = 4;
	REP(i, 1<<4) {
		int now = 0;
		REP(j, N) {
			if ((i>>now) & 1 || S[j] == s[now])
				now++;
			if (now == 4) break ;
		}
		if (now == 4)
			res = min(res, __builtin_popcount(i));
	}
	return res;
}
```