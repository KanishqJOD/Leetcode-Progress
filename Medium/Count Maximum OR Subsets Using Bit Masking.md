```cpp
class Solution {
public:
    int count(vector<int>&nums,int target,int ind, int &size,int bitwise){
        if(ind >= size){
             if(bitwise == target)return 1;
             else return 0;
        }
        int ans = 0;
        ans += count(nums,target,ind+1,size,bitwise|nums[ind]);
        ans += count(nums,target,ind+1,size,bitwise);
        return ans;
    }
    int countMaxOrSubsets(vector<int>& nums) {
        int n = nums.size();
        int maxBitwise = 0;
        for(auto &val : nums){
            maxBitwise |= val;
        }
        int ans = count(nums,maxBitwise,0,n,0);
        return ans;
    }
};
```
