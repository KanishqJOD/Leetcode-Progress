```cpp
class Solution {
    vector<int> sieve(int n) {
        vector<bool> isPrime(n + 1, true);
        isPrime[0] = isPrime[1] = false;
        for (int i = 2; i * i <= n; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j <= n; j += i) {
                    isPrime[j] = false;
                }
            }
        }
        vector<int> primes;
        for (int i = 2; i <= n; i++) {
            if (isPrime[i]) primes.push_back(i);
        }
        return primes;
    }
    
public:
    bool primeSubOperation(vector<int>& nums) { 
        vector<int> primes = sieve(1000);
        int prev = 0;
        for (int i = 0; i < nums.size(); i++) {
            int element = nums[i];
            int primeToSubtract = 0;
            for (int prime : primes) {
                if (prime < element && (element - prime) > prev) {
                    primeToSubtract = prime;
                } 
              
                else  {
                    break;
                }
            }
            nums[i] = element - primeToSubtract;
            prev = nums[i];
        }
        for (int i = 0; i < nums.size() - 1; i++) {
            if (nums[i] >= nums[i + 1]) {
                return false;
            }
        }
        return true;
    }
};
```
