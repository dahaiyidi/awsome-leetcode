## Problem

## Shortest Cycle Containing Target Node

https://binarysearch.com/problems/Shortest-Cycle-Containing-Target-Node

++

Medium

You are given a two-dimensional list of integers `graph` representing a directed graph as an adjacency list. You are also given an integer `target`.

Return the length of a shortest cycle that contains `target`. If a solution does not exist, return `-1`.

**Constraints**

- `n, m ≤ 250` where `n` and `m` are the number of rows and columns in `graph`

------

### Note

- 最短路径是典型的BFS

------

### Complexity

- 时间O：# node * # edge
- 空间O：# node

------

### Python

```python
class Sol的ution:
    def solve(self, graph, target):
        visited = set()
        q = [target]
        res = 1
        while len(q):
            # 需要层次信息，因此需要根据q的size进行遍历
            for i in range(len(q)):
                cur = q.pop(0)
                visited.add(cur)
                for nei in graph[cur]:
                    # 遍历邻居
                    if nei not in visited:
                        # 未遍历过，可以添加到q
                        q.append(nei)

                    elif nei == target:
                        # 找到target,可以返回
                        return res

            res += 1

        return -1
        

```

### C++

```C++

```



From : https://github.com/dahaiyidi/awsome-leetcode
