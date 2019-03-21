# 151. Reverse Words in a String
    Given an input string, reverse the string word by word.

**Example:**

    Example 1:
    Input: "the sky is blue"
    Output: "blue is sky the"

    Example 2:
    Input: "  hello world!  "
    Output: "world! hello"
    Explanation: Your reversed string should not contain leading or trailing spaces.

    Example 3:
    Input: "a good   example"
    Output: "example good a"
    Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.

    Note:
    A word is defined as a sequence of non-space characters.
    Input string may contain leading or trailing spaces. However, your reversed string should not contain leading or trailing spaces.
    You need to reduce multiple spaces between two words to a single space in the reversed string.

**Code:**
``` C
    class Solution {
    public:
        string reverseWords(string s) {
            if(s.length() == 0) return s;
            vector<string> v;
            string temp = "";
            for(int i = 0; s[i] != '\0'; i++){;
                if(s[i] != ' ') temp.append(1,s[i]);
                else if(s[i+1] != ' ') {
                    if(temp!="") v.push_back(temp);
                    temp = "";
                }
                if(s[i+1] == '\0' && temp!="") v.push_back(temp);
            }
            if(v.size() == 0) return "";
            int i = v.size() - 1;
            string res = v[i];
            i--;
            for(i; i >= 0; i--){
                res += ' ' + v[i];
            }
            return res;
        }
    };
```

**Submission Detail**

    Runtime: 12 ms, faster than 53.03% of C++ online submissions for Reverse Words in a String.
    Memory Usage: 11.3 MB, less than 17.35% of C++ online submissions for Reverse Words in a String.