```cpp
class Solution {
public:
    vector<int> findSubstring(string s, vector<string>& words) {
        unordered_map<string, int> counts;
        for (string word : words) counts[word]++;

        int n = s.length();
        int num = words.size();
        int len = words[0].length();

        vector<int> indexes;
        for (int i = 0; i < len; i++) {
            unordered_map<string, int> seen;
            int start = i, count = 0;
            for (int j = i; j <= n - len; j += len) {
                string word = s.substr(j, len);
                if (counts.find(word) != counts.end()) {
                    seen[word]++;
                    count++;
                    while (seen[word] > counts[word]) {
                        string leftWord = s.substr(start, len);
                        seen[leftWord]--;
                        start += len;
                        count--;
                    }
                    if (count == num) {
                        indexes.push_back(start);
                    }
                } 
                else {
                    seen.clear();
                    count = 0;
                    start = j + len;
                }
            }
        }
        return indexes;
    }
};
```
