```cpp
class Solution {
    void rec(int index,int size,int &maxi,unordered_map<string,int> &mp,string &s) {
        if(index == size) {
            int count = mp.size();
            maxi = max(maxi,count);
            return;
        }

        for(int i = index;i <size;i++) {
            string temp = s.substr(index,i - index + 1);
            if(mp.find(temp) == mp.end()) {
                mp[temp]++;
                rec(i + 1,size,maxi,mp,s);
                mp[temp]--;
                if(mp[temp] == 0) {
                    mp.erase(temp);
                }
            }
        }
    }
public:
    int maxUniqueSplit(string s) {
        unordered_map<string,int> mp;
        int maxi = -1;
        int n = s.length();
        rec(0,n,maxi,mp,s);
        return maxi;
    }
};
```
