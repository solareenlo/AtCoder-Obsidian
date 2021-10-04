# D - Grid Repainting
[[DFS]] [[BFS]] [[Green]] [[ABC]] [[Go]]
#DFS #BFS #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc088/tasks/abc088_d

## 解き方
### Code DFS
```go
package main

import "fmt"

var (
	h, w, black int
	dx          [4]int          = [4]int{1, -1, 0, 0}
	dy          [4]int          = [4]int{0, 0, 1, -1}
	s           [1001]string    = [1001]string{}
	vis         [1001][1001]int = [1001][1001]int{}
)

func dfs(x, y, black int) {
	if black >= vis[x][y] {
		return
	}
	vis[x][y] = black
	for i := 0; i < 4; i++ {
		nx, ny := x+dx[i], y+dy[i]
		if 0 <= nx && nx < h && 0 <= ny && ny < w && s[nx][ny] == '.' {
			dfs(nx, ny, black+1)
		}
	}
}

func main() {
	fmt.Scan(&h, &w)
	for i := 0; i < h; i++ {
		fmt.Scan(&s[i])
		for j := 0; j < w; j++ {
			vis[i][j] = int(1e9)
			if s[i][j] == '#' {
				black++
			}
		}
	}

	dfs(0, 0, 1)
	if res := h*w - black - vis[h-1][w-1]; res < 0 {
		fmt.Println(-1)
	} else {
		fmt.Println(res)
	}
}
```

### Code BFS
```go
package main

import (
	"container/list"
	"fmt"
)

type t struct {
	x, y, color int
}

func main() {
	var h, w int
	fmt.Scan(&h, &w)
	s := make([]string, h)
	white := 0
	for i := range s {
		fmt.Scan(&s[i])
		for j := 0; j < w; j++ {
			if s[i][j] == '.' {
				white++
			}
		}
	}

	deque := list.New()
	if s[0][0] == '.' {
		deque.PushFront(t{0, 0, 1})
	}
	black := 0
	dx := [4]int{1, -1, 0, 0}
	dy := [4]int{0, 0, 1, -1}
	for deque.Len() > 0 {
		f := deque.Remove(deque.Front()).(t)
		if f.x == h-1 && f.y == w-1 {
			black = f.color
			break
		}
		for i := 0; i < 4; i++ {
			nx, ny := f.x+dx[i], f.y+dy[i]
			if 0 <= nx && nx < h && 0 <= ny && ny < w && s[nx][ny] == '.' {
				deque.PushBack(t{nx, ny, f.color + 1})
				s[nx] = s[nx][:ny] + "#" + s[nx][ny+1:]
			}
		}
	}
	if black != 0 {
		fmt.Println(white - black)
	} else {
		fmt.Println(-1)
	}
}
```