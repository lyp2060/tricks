# tricks

## when need to shift a 2D grid, may convert it to list and then do list operation, for example:

Given a 2D grid of size n * m and an integer k. You need to shift the grid k times.

In one shift operation:

Element at grid[i][j] becomes at grid[i][j + 1].
Element at grid[i][m - 1] becomes at grid[i + 1][0].
Element at grid[n - 1][m - 1] becomes at grid[0][0].
Return the 2D grid after applying shift operation k times.

 

Example 1:


Input: grid = [[1,2,3],[4,5,6],[7,8,9]], k = 1
Output: [[9,1,2],[3,4,5],[6,7,8]]

```python
class Solution(object):
    def shiftGrid(self, grid, k):
        """
        :type grid: List[List[int]]
        :type k: int
        :rtype: List[List[int]]
        """
        n_col, n_row = len(grid[0]), len(grid)
        cache = []
        for row in grid:
            cache = cache + row
        # print(cache)
        k = k % (n_col*n_row)
        cache = cache[-k:] + cache[0:-k]
        r,c = 0, 0
        for i in cache:
            if c == len(grid[0]):
                r += 1
                c = 0
                grid[r][c] = i
            else:
                grid[r][c] = i
            c+=1
        return grid
```
