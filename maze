import random

n=5
m=10
maze = [[False for j in range(m)]for i in range(n)]

start = 0, 0
finish = n-1, m-1

for i in range(n):
  for j in range(m):
    if not (i, j) in {start, finish}:
      maze[i][j] = random.random() > 0.7
    
for i in range(n):
  for j in range(m):
    print('#' if maze[i][j] else '.', end = '')
  print()

visited = set()

def dfs(i, j, move):
  visited.add((i, j))

  if (i, j) == finish:
    print(f'found in {move} steps')
    return True
  
  delta = (1, 0), (0, 1), (-1, 0), (0, -1)
  for di, dj in delta:
    ni, nj = i + di, j + dj

    if (ni < 0) or (nj < 0) or (ni >= n) or (nj >= m):
      continue
    
    if ((ni, nj) in visited) or maze[ni][nj]:
      continue
    
    if dfs(ni, nj, move+1):
      print(f'({ni}, {nj})', end = '<-')
      return True
  
  return False

found = dfs(start[0], start[1], 0)
if not found:
  print('there is no path to target')
