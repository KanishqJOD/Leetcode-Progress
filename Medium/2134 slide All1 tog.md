```cpp
class Solution {
public:
    int minSwaps(vector<int>& nums) {
        int originalSize = nums.size();
        int cnt = 0;
        for(int i = 0; i < originalSize; i++) {
            if(nums[i] == 1) cnt++;
            nums.push_back(nums[i]);
        }

        int n = nums.size();
        int count1 = 0, count0 = 0;
        int mini = INT_MAX;

        for(int i = 0; i < cnt; i++) {
            if(nums[i] == 1) count1++;
            else count0++;
        }
        mini = min(mini, count0);
        for(int i = cnt; i < n; i++) {
            if(nums[i] == 1) count1++;
            else count0++;
            if(nums[i - cnt] == 1) count1--;
            else count0--;
            mini = min(mini, count0);
        }
        return mini;
    }
};
```

-The question was to sort all the 1s together. Initially, I thought of appending the array to itself. The main reason for this approach was that the array is circular. By appending it, we can find the minimum number of zeros, which tells us the minimum swaps required. We can use a sliding window approach to determine how many zeros are in a window of total ones.
