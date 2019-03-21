# 14. Longest Common Prefix
    Write a function to find the longest common prefix string amongst an array of strings.
    If there is no common prefix, return an empty string "".

**Example:**

    Example 1:
    Input: ["flower","flow","flight"]
    Output: "fl"

    Example 2:
    Input: ["dog","racecar","car"]
    Output: ""
    Explanation: There is no common prefix among the input strings.

    Note:
    All given inputs are in lowercase letters a-z.

**Code:**
``` C
    class Solution {
    public:
        string longestCommonPrefix(vector<string>& strs) {
            int len = strs.size();
            if(len == 0) return "";
            if(len == 1) return strs[0];
            string res=strs[0];
            for(int i = 1; i < len; i++){
                for(int j = 0; j < res.length(); j++){
                    if(res[j] != strs[i][j]){
                        res = res.substr(0,j);
                    }else if(j == strs[i].length()-1){
                        res = strs[i];
                        continue;
                    }
                }
            }
            return res;
        }
    };
```

**Submission Detail**

    Runtime: 8 ms, faster than 98.79% of C++ online submissions for Longest Common Prefix.
    Memory Usage: 9.4 MB, less than 80.26% of C++ online submissions for Longest Common Prefix.