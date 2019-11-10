---
layout: default
---

## #3. Longest Substring Without Repeating Characters

```cpp
// Cpp code with syntax highlighting.
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        //Sliding window 
        if (s.length() <= 1)
            return s.length();
        
        int hashmap[256] = {0};
        
        int begin = 0;
        int end = 0;
        int maxLenSeen = 0;
        int currentLen = 0;
        
        for(int i=0; i<s.size(); ++i)
        {
            hashmap[s[i]]++;
            // If we've already seen this value
            if (hashmap[s[i]] > 1)
            {
                end = i-1;
                //Move begin to the next possible place so that out substring defined by 
                //end-begin is of non-repeating characters again
                while(hashmap[s[i]] > 1 && begin <= end)
                {
                    hashmap[s[begin]]--;
                    begin++; //This is the beginning index for new unique string
                }
            }
            else
            {
                end = i;
            }
            currentLen = end-begin+1;
            if (currentLen > maxLenSeen) maxLenSeen = currentLen;
        }
        
        return maxLenSeen;
    }
};
```

[<back](./)