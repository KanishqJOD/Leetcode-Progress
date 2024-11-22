```cpp
class Solution {
    int  rec(int left,int right,vector<int>&nums,vector<vector<int>> &dp) {
        if(left > right) {
            return 0;
        }
        if(dp[left][right] != -1) {
            return dp[left][right];
        }
        int maxi = INT_MIN;
        for(int k = left; k <= right;k++) {
            int cost = nums[left - 1] * nums[k] * nums[right + 1] +
            rec(left,k - 1,nums,dp) + rec(k + 1,right,nums,dp);
            maxi = max(maxi,cost);
        }
        return dp[left][right] = maxi;
    }
public:
    int maxCoins(vector<int>& nums) {
        int n = nums.size();
        nums.insert(nums.begin(),1);
        nums.push_back(1);
        vector<vector<int>> dp(n+2,vector<int>(n+2,0));
        // return rec(1,n,nums,dp);

        for(int left = n;left>=1;left--){
            for(int right = 1; right<=n;right++) {
                if(left > right) {
                    continue;
                }
        int maxi = INT_MIN;
              for(int k = left; k <= right;k++) {
             int cost = nums[left - 1] * nums[k] * nums[right + 1] +
                 dp[left][k - 1] + dp[k + 1][right];
                 maxi = max(maxi,cost);
        }
        dp[left][right] = maxi;
            }
        }
        return dp[1][n];
    }
};
```
