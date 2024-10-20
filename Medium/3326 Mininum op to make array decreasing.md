```cpp

class Solution {
public:
    int minOperations(vector<int>& nums) {
        int n = nums.size();
        int operations = 0;
        vector<int> kanishq = nums;  
        
        for (int i = n - 2; i >= 0; --i) {
            if (kanishq[i] > kanishq[i + 1]) {
                int target = kanishq[i + 1];
                int opsForThisElement = 0;
                
                while (kanishq[i] > target) {
                    int gpd = greatestProperDivisorOptimized(kanishq[i]);
                    
                    if (gpd == 1) return -1;
                    
                    kanishq[i] /= gpd;
                    opsForThisElement++;
                }
                
                operations += opsForThisElement;
            }
        }
        
        return operations;
    }
    
private:
    int greatestProperDivisorOptimized(int x) {
        if (x % 2 == 0) return x / 2;
        
        for (int i = 3; i * i <= x; i += 2) {
            if (x % i == 0) return x / i;
        }
        
        return 1;
    }
};
```
