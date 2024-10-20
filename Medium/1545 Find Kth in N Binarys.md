```cpp
class Solution {
public:
    char findKthBit(int n, int k) {
        vector<string> hold;
        string prev = "0";
        hold.push_back(prev);
        
        for(int i = 1; i <= 20; i++) {
            prev += '1';
            string ans = prev;
            for(int j = prev.length() - 2; j >= 0; j--) { 
                if(prev[j] == '1') {
                    ans += '0';
                } else {
                    ans += '1';
                }
            }
            prev = ans;
            hold.push_back(ans);
        }
        string fin = hold[n - 1];  
        return fin[k - 1];  
    }
};
```
