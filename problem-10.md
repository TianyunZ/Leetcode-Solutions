---
layout: default
---

## #10. Regular Expression Matching

Solution I >> 递归

```cpp
class Solution {
public:
    bool isMatch(string s, string p) {//通过substr,让每次的比较只集中在前两个字符
        if (p.empty())
			return s.empty();
        if(p[1]=='*')
			return (isMatch(s,p.substr(2)) || ((p[0]==s[0]||p[0]=='.')&&!s.empty()&&isMatch(s.substr(1),p)));
        else
			return !s.empty()&&(p[0]==s[0]||p[0]=='.') && isMatch(s.substr(1),p.substr(1));
    }
};
```

Reference: https://blog.csdn.net/qq_40280096/article/details/82117696

假设：string s = "0123456789";

string sub1 = s.substr(5); //只有一个数字5表示从下标为5开始一直到结尾：sub1 = "56789"

string sub2 = s.substr(5, 3); //从下标为5开始截取长度为3位：sub2 = "567"

Solution II >> DP动态规划

```cpp

```


[back](./)