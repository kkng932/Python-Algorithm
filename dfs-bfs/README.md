# DFS(Depth-First Search, 깊이 우선 탐색)  

그래프에서 깊은 부분을 우선적으로 탐색한다.  
stack, 재귀함수를 사용한다.  

1. 탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.  
2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 그 인저 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 인접 노드가 없으면 최상단 노드를 꺼낸다.  
3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다. 

```python
# DFS 메서드 정의  
def dfs(graph, v, visited):
    # 현재 노드를 방문 처리  
    visited[v] = True
    print(v, end=' ')
    # 현재 노드와 연결된 다른 노드를 재귀적으로 방문 
    for i in graph[v]:
        if not visited[i]:
            dfs(graph, i, visited)
            
# 각 노드가 연결된 정보를 리스트 자료형으로 표현(2차원 리스트) 
graph = [
    [],
    [2, 3, 8],
    [1, 7],
    [1, 4, 5],
    [3, 5],
    [3, 4],
    [7],
    [2, 6, 8],
    [1, 7]
    ]
    
# 각 노드가 방문된 정보를 리스트 자료형으로 표현(1차원 리스트)  
visited = [False] * 9

# 정의된 DFS 함수 호출  
dfs(graph, 1, visited)
```
#### 사용 예시  
아래와 같은 정보가 주어지고 0이 붙어있는 것을 한 덩어리로 보고 그 개수를 구하여야 할 때  
```
00110
00011
11111
00000
```
dfs 방식으로 구현했을 때:  
1. 특정한 지점의 주변 상, 하, 좌, 우를 살펴본 뒤에 주변 지점 중에서 값이 '0'이면서 아직 방문하지 않은 지점이 있다면 해당 지점을 방문한다.
2. 방문한 지점에서 다시 상, 하, 좌, 우를 살펴보면서 방문을 다시 진행하면, 연결된 모든 지점을 방문할 수 있다.  
3. 1~2번의 과정을 모든 노드에 반복하며 방문하지 않은 지점의 수를 센다.  


# BFS(Breadth First Search, 너비 우선 탐색)  

가까운 노드부터 탐색하는 알고리즘
queue, while문을 사용한다.

1. 탐색 시작 노드를 큐에 삽입하고 방문 처리를 한다.  
2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리를 한다.  
3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다. 

최소 거리를 구할 때 효과적이다. 가까운 노드부터 차례대로 그래프의 모든 노드를 탐색하기 때문이다. 

```pythonfrom collections import deque

# define BFS method
def bfs(graph, start, visited):
    # use dequeue library for implement queue
    queue = deque([start])
    # visit current node 
    visited[start] = True
    # loop until queue is empty 
    while queue:
        # print one in queue
        v = queue.popleft()
        print(v, end=' ')
        # insert in queue unvisited elements linked that
        for i in graph[v]:
            if not visited[i]:
                queue.append(i)
                visited[i] = True

# express information linking each node to list
graph = [
    [],
    [2, 3, 8],
    [1, 7],
    [1, 4, 5],
    [3, 5],
    [3, 4],
    [7],
    [2, 6, 8],
    [1, 7]
]

# express information about each node visited to list
visited = [False] * 9

# call defined BFS method
bfs(graph, 1, visited)
```
