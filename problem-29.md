---
layout: default
2019-11-15
---

## #29. Divide Two Integers

```cpp
class Solution {
public:
    int divide(int dividend, int divisor) {
        int index = 1;
        if (dividend == INT_MIN && divisor == -1)
            return INT_MAX;
        if ( (dividend > 0) == (divisor < 0) )
            index = -1;
        if (dividend > 0)
            dividend *= -1;
        if (divisor > 0)
            divisor *= -1;
        if (dividend > divisor)
            return 0;
        long count = 1;
        long ans = 0;
        long d = divisor;
        while (1) {
            if (dividend < 0 && (dividend - d) <= 0) {
                dividend -= d;
                ans += count;
                count += count;
                d += d;
            }
            else {
                if (d == divisor)
                    break;
                d = divisor;
                count = 1;
            }
        }
        
        return ans*index;
    }
};
```

[<back](./)