```cpp
class Solution {
public:
    string minWindow(string s, string t) {

        unordered_map<char, int> m;
        for (int i = 0; i < t.size(); i++) {
            m[t[i]]++;
        }
        
        int left = 0;
        int right = 0;
        int counter = t.size();
        
        int minStart = 0;
        int minLength = INT_MAX;
        
        while (right < s.size()) {
 
            if (m[s[right]] > 0) {
                counter--;
            }
       
            m[s[right]]--;
            right++;
            while (counter == 0) {
                if (right - left < minLength) {
                    minStart = left;
                    minLength = right - left;
                }
                
                m[s[left]]++;
                if (m[s[left]] > 0) {
                    counter++;
                }
                left++;
            }
        }
        
        if (minLength != INT_MAX) {
            return s.substr(minStart, minLength);
        }
        return "";
    }
};
```
