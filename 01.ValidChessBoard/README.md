## Valid Chess Board
You are given a tiled chart paper of N rows and M columns. There are a total of N X M tiles in it. Each tile is colored either black or white. Now, you need to count how many ways are there to cut valid chessboards of size 8 X 8 out of this chart paper. 

#### Notes

1. One chessboard is different from another if either of them contains at least one tile which is different from another chessboard.    
2. The chess board formation should have distinct colors of adjacent cells i.e. Black
    
White alternative (regular chessboard rules apply).

#### Input Format

The first line contains two space-separated integers N and M as input.
In the next N lines, you are given a string of M characters. Each character is either 0 or 1. If it is 0 then the tile color is white, if it is 1 then the tile color is black.

#### Output Format
In the output, you need to print an integer that denotes the required count as stated in the problem statement.

#### Constraints
1<=n, m>=1000

```
Input:
9 9
010101010
101010101
010101010
101010101
010101010
101010101
010101010
101010101
010101010
```
```
output:
4
```
#### Solution:
```c++
#include <bits/stdc++.h>
using namespace std;
const int N = 1005;
string mat[N];
bool f(int x, int y, int n, int m) {
    for(int i = x; i < x + 8; i ++) {
        for(int j = y; j < y + 7; j ++) {
            if(mat[i][j] == mat[i][j + 1] || (i < x + 7 && mat[i][j] == mat[i + 1][j]))
                return 0;
        }
    }
    return 1;
}
int main() {

    int n, m;
    cin >> n >> m;
    for(int i = 0; i < n; i ++)
        cin >> mat[i];
    int cnt = 0;
    for(int i = 0; i < n; i ++) {
        for(int j = 0; j < m; j ++) {
            if(i + 8 <= n && j + 8 <= m && f(i, j, n, m))
                cnt ++;
        }
    }
    cout << cnt;
    return 0;
}
```
