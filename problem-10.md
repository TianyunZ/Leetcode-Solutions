---
layout: default
---

## #10. Regular Expression Matching

Solution I >> 递归

```cpp
class Solution {
public:
    bool isMatch(string s, string p) {//通过substr,让每次的比较只集中在前两个字符
        if(p.empty()) return s.empty();
        if(p[1]=='*') return (isMatch(s,p.substr(2)) || ((p[0]==s[0]||p[0]=='.')&&!s.empty()&&isMatch(s.substr(1),p)));
        else return !s.empty()&&(p[0]==s[0]||p[0]=='.') && isMatch(s.substr(1),p.substr(1));
    }
};
```

Solution II >> DP动态规划

```cpp

```


[back](./)