# 5. Longest Palindromic Substring
    Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

**Example:**

    Example 1:
    Input: "babad"
    Output: "bab"
    Note: "aba" is also a valid answer.

    Example 2:
    Input: "cbbd"
    Output: "bb"

**Code:**
``` C
    class Solution {
    public:
        string midToSide(string s, int left, int right){
            while(left >= 0 && right < s.length() && s[left] == s[right]){
                left--;
                right++;
            }
            return s.substr(left+1,right-left-1); 
        }
        string longestPalindrome(string s) {
            int len = s.length();
            if(len == 0) return "";
            string res = s.substr(0,1);
            for(int i = 0; i <= len-2; i++){
                string t = midToSide(s,i,i);
                if(t.length() > res.length())
                    res = t;
                t = midToSide(s,i,i+1);
                if(t.length() > res.length())
                    res = t;
            } 
            return res;
        }
    };
```

**Submission Detail**

    Runtime: 84 ms, faster than 51.19% of C++ online submissions for Longest Palindromic Substring.
    Memory Usage: 120.3 MB, less than 17.34% of C++ online submissions for Longest Palindromic Substring.