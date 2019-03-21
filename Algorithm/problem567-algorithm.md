# 567. Permutation in String
    Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.

**Example:**

    Example 1:
    Input:s1 = "ab" s2 = "eidbaooo"
    Output:True
    Explanation: s2 contains one permutation of s1 ("ba").

    Example 2:
    Input:s1= "ab" s2 = "eidboaoo"
    Output: False

**Note:**
    The input strings only contain lower case letters.
    The length of both given strings is in range [1, 10,000].

**Code:**
``` C
    class Solution {
    public:
        bool checkInclusion(string s1, string s2) {
            if(s1.length() == 0 || s1.length() > s2.length()) return false;
            vector<int> v1(26), v2(26);
            for(int i = 0; i < s1.length(); i++){
                v1[s1[i] - 'a']++;
                v2[s2[i] - 'a']++;	
            }
            if(v1 == v2) return true;
            for(int i = 0; i + s1.length() < s2.length(); i++){
                v2[s2[i] - 'a']--;
                v2[s2[i+s1.size()]-'a']++;
                if(v1 == v2) return true;
            }

            return false;
        }
    };

```

**Submission Detail**

    Runtime: 20 ms, faster than 43.38% of C++ online submissions for Permutation in String.
    Memory Usage: 9.8 MB, less than 96.94% of C++ online submissions for Permutation in String.