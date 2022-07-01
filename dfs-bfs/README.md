DFS(Depth-First Search, 깊이 우선 탐색)
========================================
그래프에서 깊은 부분을 우선적으로 탐색한다.
stack, 재귀함수를 사용한다.

1. 탐색 시작 노드를 스택에 삽입, 방문처리
2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 스택에 삽입, 방문처리 
   방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼냄
3. 2번 불가능할 때까지 반복

```python
def dfs(graph, v, visited):
    visited[v] = True
    print(v, end='')
    for i in graph[v]:
        if not visited[i]:
            dfs(graph, i, visited)

if __name__ == "__main__":
    # 노드 i가 인접한 노드가 graph[i]에 서로 저장되어 있어야 한다.
    graph = [
        [],
        [2, 3, 8],
        [1, 7],
        [1, 4, 5]
        [3, 5],
        [3, 4],
        [7],
        [2, 6, 8],
        [1, 7]
    ]
    visited = [False] * 9
    dfs(graph, 1, visited)
```


BFS(Breadth First Search, 너비 우선 탐색)
================================================
가까운 노드부터 탐색하는 알고리즘
queue, while문을 사용한다.

1. 큐에 탐색 시작 노드 삽입, 방문 처리
2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중 방문하지 않은 노드를 모두 큐에 삽입, 방문 처리
3. 큐에 노드가 남지 않을 때까지 2번 반복

최소 거리를 구할 때 효과적이다. 가까운 노드부터 차례대로 그래프의 모든 노드를 탐색하기 때문이다. 

from collections import deque

from collections import deque

n, m = map(int, input().split())
dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]
graph = []
for i in range(n):
    graph.append(list(map(int, input())))

```python
def bfs(x, y):
    queue = deque()
    queue.append(x, y)
    # 큐가 빌 때까지 반복
    while queue:
        x, y = queue.popleft()
        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]
            # 미로를 벗어난 경우
            if nx < 0 or ny < 0 or nx >= n or ny >= m:
                continue
            # 벽인 경우
            if graph[nx][ny] == 0:
                continue
            # 해당 노드를 처음 방문하는 경우에 최단 거리 기록
            if graph[nx][ny] == 1:
                graph[nx][ny] = graph[x][y]+1
                queue.append((nx, ny))
    return graph[n-1][m-1]


print(bfs(0, 0))
```
