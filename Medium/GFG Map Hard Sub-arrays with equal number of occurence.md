```cpp
class Solution {
  public:
    int sameOccurrence(vector<int>& arr, int x, int y) {
        int n = arr.size();
    unordered_map<int, int> mp;
    mp[0] = 1;  
    int balance = 0, count = 0;
    
    for (int i = 0; i < n; i++) {
        if (arr[i] == x) balance++;
        if (arr[i] == y) balance--;
        count += mp[balance];
        mp[balance]++;
    }
    
    return count;
    }
};
```
