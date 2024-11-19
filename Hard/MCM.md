```cpp
class Solution {
    int rec(int i, int j ,vector<int> &arr,vector<vector<int>> &dp) {
        if(i == j) {
            return 0;
        }
        if(dp[i][j] != -1) {
            return dp[i][j];
        }
        int mini = INT_MAX;
        for(int k = i; k <j;k++) {
            int op = (arr[i-1] * arr[k] * arr[j]) +
            rec(i,k,arr,dp) + rec(k + 1, j , arr,dp);
            mini = min(mini,op);
        }
        return dp[i][j] = mini;
    }
  public:
int matrixMultiplication(vector<int> &arr) {
    int n = arr.size();
    vector<vector<int>> dp(n+1, vector<int>(n+1, 0));
    
    for (int i = n - 1; i >= 1; i--) {
        for (int j = 1; j < n; j++) {               
            int mini = INT_MAX;
            if(i >=j) {
                continue;
            }
            for (int k = i; k < j; k++) { 
                int op = (arr[i - 1] * arr[k] * arr[j]) + dp[i][k] + dp[k + 1][j];
                mini = min(mini, op);
            }
            dp[i][j] = mini;
        }
    }
    return dp[1][n - 1];
}
};
```
