def solution(n, results):
    answer = 0
    INF = int(1e9)
    graph = [[INF] * (n + 1) for _ in range(n + 1)]
    for i in range(1, n + 1):
        graph[i][i] = 0
    for i in results:
        graph[i[1]][i[0]] = 1
    for i in range(1, n + 1):
        for j in range(1, n + 1):
            for k in range(1, n + 1):
                if graph[j][i] + graph[i][k] == 2:
                    graph[j][k] = 1
    count = [0] * (n + 1)
    for i in range(1, n + 1):
        for j in range(1, n + 1):
            if i == j:
                continue
            if graph[i][j] == 1:
                count[i] += 1
                count[j] += 1
    for i in count:
        if i == n - 1:
            answer += 1
    return answer