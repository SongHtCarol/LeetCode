# 516. Longest Palindromic Subsequence
    Given a string s, find the longest palindromic subsequence's length in s. You may assume that the maximum length of s is 1000.

**Example:**

    Example 1:
    Input:
    "bbbab"
    Output:
    4
    One possible longest palindromic subsequence is "bbbb".

    Example 2:
    Input:
    "cbbd"
    Output:
    2
    One possible longest palindromic subsequence is "bb".

**Code:**
``` C
    class Solution {
    public:
        int longestPalindromeSubseq(string s) {
        int len = s.length();
            vector<vector<int>> dp(len,vector<int>(len));
            for(int i = len-1; i >= 0; i--){
                dp[i][i] = 1;
                for(int j = i+1; j < len; j++){
                    if(s[i] == s[j]) dp[i][j] = dp[i+1][j-1] + 2;
                    else dp[i][j] = max(dp[i][j-1], dp[i+1][j]);
                }
            }
            return dp[0][len-1]; 
        }
    };

```

**Submission Detail**

    Runtime: 84 ms, faster than 81.85% of C++ online submissions for Longest Palindromic Subsequence.
    Memory Usage: 69.6 MB, less than 63.03% of C++ online submissions for Longest Palindromic Subsequence.