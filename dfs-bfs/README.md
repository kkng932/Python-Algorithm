# DFS(Depth-First Search, 깊이 우선 탐색)
========================================
# 그래프에서 깊은 부분을 우선적으로 탐색한다.
# stack, 재귀함수를 사용한다.

# 1. 탐색 시작 노드를 스택에 삽입, 방문처리
# 2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 스택에 삽입, 방문처리
#    방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼냄
# 3. 2번 불가능할 때까지 반복


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