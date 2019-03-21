# 42. Multiply Strings
    Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.
**Example:**

    Example 1:
    Input: num1 = "2", num2 = "3"
    Output: "6"

    Example 2:
    Input: num1 = "123", num2 = "456"
    Output: "56088"
    
    Note:
    The length of both num1 and num2 is < 110.
    Both num1 and num2 contain only digits 0-9.
    Both num1 and num2 do not contain any leading zero, except the number 0 itself.
    You must not use any built-in BigInteger library or convert the inputs to integer directly.

**Code:**
``` C
    class Solution {
    public:
        string multiply(string num1, string num2) {
            string res = "";
            reverse(num1.begin(), num1.end());
            reverse(num2.begin(), num2.end());
            int len1 = num1.length(), len2 = num2.length();
            vector<int> v(len1+len2,0);
            for(int i = 0; i < len1; i++){
                for(int j = 0; j < len2; j++){
                    int temp = v[i+j] + (num1[i]-'0') * (num2[j]-'0');
                    v[i+j] = temp%10;
                    v[i+j+1] += temp/10;
                }
            }
            int flag = 0;
            for(int i = len1+len2-1; i >= 0; i--){
                if(flag == 0 && v[i] != 0) flag = 1;
                if(flag == 1) res += v[i] + '0';
            }
            if(flag == 0) res="0";
            return res;
        }
    };
```

**Submission Detail**

    Runtime: 16 ms, faster than 41.39% of C++ online submissions for Multiply Strings.
    Memory Usage: 10.8 MB, less than 36.19% of C++ online submissions for Multiply Strings.