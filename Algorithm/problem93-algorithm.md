# 93. Restore IP Addresses
    Given a string containing only digits, restore it by returning all possible valid IP address combinations.

**Example:**

    Example :
    Input: "25525511135"
    Output: ["255.255.11.135", "255.255.111.35"]


**Code:**
``` C
    class Solution {
    public:
        bool isValid(string s){
            int len = s.length();
            return (len > 0 && len < 4 && (s[0] != '0' || len == 1) && stoi(s) <= 255);
        }
        vector<string> restoreIpAddresses(string s) {
            vector<string> v;
            int len = s.length();
            for(int i = 1; i <= 3 && i <= len - 3; i++){
                for(int j = 1; j <= 3 && j <= len - i - 2; j++){
                    for(int k = 1; k <= 3 && k <= len - i - j - 1; k++){
                        string s1 = s.substr(0,i), s2 = s.substr(i,j), s3 = s.substr(i+j,k), s4 = s.substr(i+j+k,len-i-j-k);
                        if(isValid(s1) && isValid(s2) && isValid(s3) && isValid(s4))
                            v.push_back(s1+"."+s2+"."+s3+"."+s4);
                    }
                }
            }
            return v;
        }
    };
```

**Submission Detail**

    Runtime: 4 ms, faster than 100.00% of C++ online submissions for Restore IP Addresses.
    Memory Usage: 8.3 MB, less than 96.77% of C++ online submissions for Restore IP Addresses.