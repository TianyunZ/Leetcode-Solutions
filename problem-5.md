---
layout: default
---


## #5. Longest Palindromic Substring

Solution I.Dynamic Programming
当str[i]=str[j]时，如果str[i+1...j-1]是回文串，则str[i...j]也是回文串；如果str[i+1...j-1]不是回文串，则str[i...j]不是回文串
```cpp
// Cpp code with syntax highlighting.
string longestPalindrome(string s)
{
    if (s.empty()) return "";
    int len = s.size();
    if (len == 1)return s;
    int longest = 1;
    int start=0;
    vector<vector<int> > dp(len,vector<int>(len));
    for (int i = 0; i < len; i++)
    {
        dp[i][i] = 1;
        if(i<len-1)
        {
            if (s[i] == s[i + 1])
            {
                dp[i][i + 1] = 1;
                start=i;
                longest=2;
            }
        }
    }
    for (int l = 3; l <= len; l++)//子串长度
    {
        for (int i = 0; i+l-1 < len; i++)//枚举子串的起始点
        {
            int j=l+i-1;//终点
            if (s[i] == s[j] && dp[i+1][j-1]==1)
            {
                dp[i][j] = 1;
                start=i;
                longest = l;
            }
        }
    }
    return s.substr(start,longest);
}
```
Solution II.
```cpp
class Solution {
public:
    int expandAroundCentre(string s, int left, int right) {
        int L = left, R = right;
        while (L>=0 && R<s.size() && s[L] == s[R]) {
            L--;
            R++;
        }
        return R-L-1;
    }
    
public:
    string longestPalindrome(string s) {
        int stt = 0;
        int end = 0;
        for (int i = 0; i < s.size(); i++) {
            int len1 = expandAroundCentre(s, i, i);
            int len2 = expandAroundCentre(s, i, i+1);
            int len = max(len1, len2);
            if (len > end-stt) {
                stt = i - (len-1) / 2;
                end = i + len / 2;
            }
        }
        return s.substr(stt, end-stt+1);
    }
};
```
[<back](./)
