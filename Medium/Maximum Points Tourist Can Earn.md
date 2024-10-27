```cpp
class Solution {
public:

int dfs(int day, int currentCity, int k, vector<vector<int>>& stayScore, vector<vector<int>>& travelScore, vector<vector<int>>& memo) {
    if (day == k) return 0;

    if (memo[day][currentCity] != -1) return memo[day][currentCity];

    int maxPoints = stayScore[day][currentCity] + dfs(day + 1, currentCity, k, stayScore, travelScore, memo);
    
    for (int nextCity = 0; nextCity < travelScore.size(); nextCity++) {
        if (nextCity != currentCity) {
            maxPoints = max(maxPoints, travelScore[currentCity][nextCity] + dfs(day + 1, nextCity, k, stayScore, travelScore, memo));
        }
    }
    return memo[day][currentCity] = maxPoints;
}
    int maxScore(int n, int k, vector<vector<int>>& stayScore, vector<vector<int>>& travelScore) {
          vector<vector<int>> memo(k, vector<int>(n, -1));
    
    int maxPoints = 0;
    
    for (int startCity = 0; startCity < n; startCity++) {
        maxPoints = max(maxPoints, dfs(0, startCity, k, stayScore, travelScore, memo));
    }
    
    return maxPoints;
    }
};
```
