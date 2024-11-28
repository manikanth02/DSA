https://leetcode.com/problems/path-with-maximum-gold/


Intuition::

Start/Take each elements as starting point of goldmine process and go on each possible path and calculate
maxium gold you can  obtain.So,basically we are going to do depth first seach for each elemet which is not equal to 0


```

class Solution {
public:

    vector<int> roww = {1, -1, 0, 0};


    vector<int> coll = {0, 0, -1, 1};

    int depth(vector<vector<int>>& grid,int x, int y, int row,int col){
    if(x < 0 || x >= row || y < 0 || y >= col || grid[x][y] == 0 )return 0;
    int curr = grid[x][y];
    grid[x][y] = 0;
    int localMaxmGlod = curr;
    for(int i = 0; i < 4; i++){
        int newX = x + roww[i];
        int newY = y + coll[i];
        localMaxmGlod = max(localMaxmGlod, curr + depth(grid,newX,newY,row,col));
    }
    grid[x][y] = curr;
    return localMaxmGlod;
    }


    int getMaximumGold(vector<vector<int>>& grid) {
        int maxmGold = 0;
        int row = grid.size();
        int col = grid[0].size();

    for(int i = 0; i < row; i++){
    for(int j = 0; j < col; j++){
        if(grid[i][j] != 0){
            maxmGold = max(maxmGold,depth(grid,i,j,row,col));
        }
    }
    }
    return maxmGold;
    }
};

```
