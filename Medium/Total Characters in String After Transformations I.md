```cpp
class Solution {
public:
#define ll long long
#define inp(v) for(auto &it: v) cin>>it
#define pyes cout <<"YES\n";
#define pno cout <<"NO\n";
#define pb push_back
#define pii pair<int,int>
#define vi vector<int>
#define vll vector<long long>
#define all(x) x.begin(),x.end()
#define INF INT_MAX
#define MOD 1000000007
    int lengthAfterTransformations(string s, int t) {
        vll prev(26,0);
        for(int i = 0; i<s.length();i++) {
            prev[s[i] -'a']++;
        }
        while(t--) {
            vll curr(26,0);
            for(int i = 0; i<26;i++) {
                if(i == 25) {
                     curr[0] = (prev[i] + curr[0]) % MOD;
                     curr[1] = (prev[i] + curr[1]) % MOD;
                }
                else {
                    curr[i+1] = (curr[i+1] + prev[i]) % MOD;
                }
            }
            prev = curr;
        }
        ll ans = 0;
        for(auto &it : prev) {
            ans += it;
            
        }
        return (ans)%MOD;
    }
};
```
