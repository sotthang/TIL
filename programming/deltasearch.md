# 델타탐색

## 델타탐색 이란

2차원 리스트에서 상하좌우 또는 상하좌우 + 좌상좌하우상우하 를 탐색할 때 사용

index 를 벗어날 수 있을 땐 조건문으로 컨트롤 가능

델타탐색 상하좌우

```python
two_d_list = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]

for i in range(4):    # two_d_list[1][1] 의 상하좌우
    dx_x = 1 + dx[i]
    dy_y = 1 + dy[i]
    print(two_d_list[dx_x][dy_y])

>>> 2
    8
    4
    6

for i in range(4):    # two_d_list[2][2] 의 상하좌우
    dx_x = 2 + dx[i]
    dy_y = 2 + dy[i]
    if dx_x < 0 or dy_y < 0 or dx_x > 2 or dy_y > 2:
        print('out')
    else:
        print(two_d_list[dx_x][dy_y])

>>> 6
    out
    8
    out
```

델타탐색 상하좌우 + 좌상좌하우상우하

```python
two_d_list = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12], 
    [13, 14, 15, 16]
]

dx = [-1, 1, 0, 0, -1, 1, -1, 1]
dy = [0, 0, -1, 1, -1, -1, 1, 1]

for i in range(8):    # two_d_list[1][1] 의 상하좌우 + 좌상좌하우상우하
    dx_x = 1 + dx[i]
    dy_y = 1 + dy[i]
    print(two_d_list[dx_x][dy_y])

>>> 2
    10
    5
    7
    1
    9
    3
    11

for i in range(8):    # two_d_list[3][3] 의 상하좌우 + 좌상좌하우상우하
    dx_x = 3 + dx[i]
    dy_y = 3 + dy[i]
    if dx_x < 0 or dy_y < 0 or dx_x > 3 or dy_y > 3:
        print('out')
    else:
        print(two_d_list[dx_x][dy_y])

>>> 12
    out
    15
    out
    11
    out
    out
    out
```
