```cpp
class Solution {
public:
    void solveSudoku(vector<vector<char>>& board) {
        solve(board);
    }

    bool solve(vector<vector<char>>& board) {
        for (int r = 0; r < 9; r++) {
            for (int c = 0; c < 9; c++) {
                if (board[r][c] == '.') {
                    for (char digit = '1'; digit <= '9'; digit++) {
                        if (isTrue(board, r, c, digit)) {
                            board[r][c] = digit;
                            if (solve(board)) return true;
                            board[r][c] = '.';
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }

    bool isTrue(vector<vector<char>>& board, int r, int c, char digit) {
        for (int i = 0; i < 9; i++) {
            if (board[r][i] == digit || board[i][c] == digit) return false;
        }
        int boxRow = (r / 3) * 3, boxCol = (c / 3) * 3;
        for (int i = boxRow; i < boxRow + 3; i++) {
            for (int j = boxCol; j < boxCol + 3; j++) {
                if (board[i][j] == digit) return false;
            }
        }
        return true;
    }
};

```
