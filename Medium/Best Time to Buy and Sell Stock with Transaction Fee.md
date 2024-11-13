```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
         int n = prices.size();

        vector<int> front1(2, 0); 
        vector<int> curr(2, 0);   
        int k = fee;
        for(int index = n - 1; index >= 0; index--) {
            for(int buy = 0; buy <= 1; buy++) {
                int profit = 0;
                if(buy) {
                    profit = max(-prices[index]  + front1[0],  
                               0 + front1[1]);             
                }
                else {
                    profit = max(prices[index] - fee + front1[1],   
                               0 + front1[0]);               
                }
                curr[buy] = profit;
            }
            front1 = curr;
        }
        return curr[1];
    }
};
```
