---
layout: default
---

## #7. Reverse Integer

```cpp
class Solution {
public:
    int reverse(int x) {
        int index = 1;
        if (x == INT_MIN)
            return 0;
        if (x < 0) {
            index = -1;
            x = x*(-1);
        }
        string s = to_string(x);
        cout << s;
        long long rst = 0;
        int fin = 0;
        int size = s.size();
        // cout << size;
        for (int i = 0; i < size; i ++) {
            rst += (s[size-1-i]-'0')*pow(10,size-1-i);
        }
        rst *= index;
        if (rst > INT_MAX || rst < INT_MIN)
            fin = 0;
        else
            fin = rst;
        return fin;
    }
};
```
[back](./)