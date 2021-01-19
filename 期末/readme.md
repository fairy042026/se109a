# 李氏演算法求迷宮中的最短路徑

為什麼選擇這個主題，是因為一開始看到它的名稱叫lee algorithm，覺得滿特別的，就選了這個主題。剛好看到它是走迷宮的，覺得滿有趣的，之前我有稍微去查了一下深度學習的資料，其中有一個主題和迷宮挺像的，就是人物會自己嘗試去走迷宮，經過不斷嘗試走到終點，而這個是找尋最短路徑，雖然不一樣，不過還是挺有意思的。

## 程式碼

```
from collections import deque
 
 
#下面列出了來自一個單元格的所有4種可能的移動方式

row = [-1, 0, 0, 1]
col = [0, -1, 1, 0]
 
 
#檢查是否可以從當前位置移至位置（行，列）的功能。
#如果row，col不是有效位置或值為0或已被訪問，則該函數返回false
def isValid(mat, visited, row, col):
    return (row >= 0) and (row < M) and (col >= 0) and (col < N) \
           and mat[row][col] == 1 and not visited[row][col]
 
 
#在源單元格（i，j）的矩陣矩陣中查找最短可能路線到目標單元格（x，y）
def BFS(mat, i, j, x, y):
 
#構造矩陣以跟踪訪問的單元格
    visited = [[False for x in range(N)] for y in range(M)]
 
#創建一個空佇列
    q = deque()
 
#將源單元格標記為已訪問並排隊源節點
    visited[i][j] = True

#（i，j，dist）表示矩陣單元格坐標及其與源的最小距離
    q.append((i, j, 0))
 
#儲存從源到目標的最長路徑的長度
    min_dist = float('inf')
 
#循環直到佇列為空
    while q:
 
#從隊列中彈出節點並對其進行處理
        (i, j, dist) = q.popleft()
 
#（i，j）表示當前單元格，並且dist存儲其距源的最小距離
 
#如果找到目標，則更新min_dist並停止
        if i == x and j == y:
            min_dist = dist
            break
 
#檢查當前單元格中所有4種可能的運動，並從當前位置開始對每個有效運動（i + row [k]，j + col [k]）進行排隊
        for k in range(4):
#檢查是否可以轉到位置（i + row [k]，j + col [ k]）從當前位置
            if isValid(mat, visited, i + row[k], j + col[k]):

#將下一個單元格標記為已訪問並將其排隊
                visited[i + row[k]][j + col[k]] = True
                q.append((i + row[k], j + col[k], dist + 1))
 
    if min_dist != float('inf'):
        print("The shortest path from source to destination has length", min_dist)
    else:
        print("Destination can't be reached from given source")
 
 
#在a中的最短路徑迷宮
if __name__ == '__main__':
 
    #輸入迷宮
    mat = [
        [1, 1, 1, 1, 1, 0, 0, 1, 1, 1],
        [0, 1, 1, 1, 1, 1, 0, 1, 0, 1],
        [0, 0, 1, 0, 1, 1, 1, 0, 0, 1],
        [1, 0, 1, 1, 1, 0, 1, 1, 0, 1],
        [0, 0, 0, 1, 0, 0, 0, 1, 0, 1],
        [1, 0, 1, 1, 1, 0, 0, 1, 1, 0],
        [0, 0, 0, 0, 1, 0, 0, 1, 0, 1],
        [0, 1, 1, 1, 1, 1, 1, 1, 0, 0],
        [1, 1, 1, 1, 1, 0, 0, 1, 1, 1],
        [0, 0, 1, 0, 0, 1, 1, 0, 0, 1]
    ]
 
    #M x N矩陣
    M = N = 10
 
    #查找從源（0，0）到目標（7，5）的最短路徑
    BFS(mat, 0, 0, 5, 4)
    
```

## 執行結果
**(0,0)到(5,4)的最短路徑
![9](https://github.com/fairy042026/se109a/blob/master/%E6%9C%9F%E6%9C%AB/9.PNG)


參考資料：https://www.techiedelight.com/lee-algorithm-shortest-path-in-a-maze/

