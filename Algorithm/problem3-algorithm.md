# 3. Longest Substring Without Repeating Characters
    Given a string, find the length of the longest substring without repeating characters.

**Example:**

    Example 1:
    Input: "abcabcbb"
    Output: 3 
    Explanation: The answer is "abc", with the length of 3. 

    Example 2:
    Input: "bbbbb"
    Output: 1
    Explanation: The answer is "b", with the length of 1.

    Example 3:
    Input: "pwwkew"
    Output: 3
    Explanation: The answer is "wke", with the length of 3. 
    Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

**Code:**
``` C
    class Solution {
    public:
        unordered_map<char,int> m;
        void deleteMapData(int start, int end, string s){
            for(int i = start; i <= end; i++){
                m.erase(s[i]);
            }
        }
        int lengthOfLongestSubstring(string s) {
            int res = 1, temp = 1;
            int left = 0, right = 0;
            int cur = 0;
            int len = s.length();
            if(len==0) return 0;
            while(cur != len){
                if(cur == 0) {
                    m[s[cur]] = 0;
                }
                else{
                    if(m.count(s[cur]) < 1){
                        m[s[cur]] = cur;
                        temp += 1;
                    }else{
                        res = res > temp ? res : temp;
                        int templeft = left, tempright = m[s[cur]];
                        left = m[s[cur]]+1;
                        deleteMapData(templeft,tempright,s);
                        m[s[cur]] = cur;
                        temp = temp - (tempright - templeft + 1) +1;
                    }
                }
                cur++;
            }
            return res = res > temp ? res : temp;
        }
    };
```

**Submission Detail**

    Runtime: 268 ms, faster than 12.26% of C++ online submissions for Longest Substring Without Repeating Characters.
    Memory Usage: 330.6 MB, less than 5.03% of C++ online submissions for Longest Substring Without Repeating Characters.