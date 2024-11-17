```cpp
class Solution {
    // int rec(int ind, int prev,int n,vector<int> &nums,vector<vector<int>>& dp) {
    //     if(ind == n) {
    //         return 0;
    //     }
    //     if(dp[ind][prev + 1] != -1) {
    //         return dp[ind][prev + 1];
    //     }
    //     int notPick = 0 + rec(ind + 1,prev,n,nums,dp);
    //     int pick = -1;
    //     if(prev == -1  ||( (nums[prev] < nums[ind]) && (nums[ind] % nums[prev]) == 0) ) {
    //         pick = 1 + rec(ind + 1,ind,n,nums,dp);
    //     }
    //     return dp[ind][prev + 1] = max(notPick,pick);
    // }
public:
    vector<int> largestDivisibleSubset(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int n = nums.size();
        vector<int> dp(n,1);
        vector<int> parent(n,-1);
        int maxi  = -1;
        int maxIndex = 0;
        for(int index = 0; index<n;index++) {
            for(int prev = 0; prev <index;prev++) {
                  if(nums[index] % nums[prev] == 0 && dp[index] < dp[prev] + 1) {
                    dp[index] = dp[prev] + 1;
                    parent[index] = prev;
                  }
            }
            if(dp[index] > maxi) {
                maxi = dp[index];
                maxIndex = index;
                            }
        }
        vector<int> ans;
        for(int i = maxIndex; i>=0;i = parent[i]) {
ans.push_back(nums[i]);
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
