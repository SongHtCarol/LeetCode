# 69. Sqrt(x)
    Implement int sqrt(int x).
    Compute and return the square root of x, where x is guaranteed to be a non-negative integer.

    Since the return type is an integer, the decimal digits are truncated and only the integer part of the result is returned.

**Example:**

    Example 1:
    Input: 4
    Output: 2

    Example 2:
    Input: 8
    Output: 2

    Explanation: The square root of 8 is 2.82842..., and since 
                the decimal part is truncated, 2 is returned.

**Code:**
``` C
    class Solution {
    public:
        int mySqrt(int x) {
                int left = 1, right = 46340;
                while(left < right){
                    int mid = (left + right) / 2;
                    if(mid*mid < x) left = mid + 1;
                    else if(mid*mid > x) right = mid - 1;
                    else return mid;
                }
                if(left*left > x) return left-1;
                else return left;
            }
    };
```

**Submission Detail**

    Runtime: 12 ms, faster than 98.99% of C++ online submissions for Sqrt(x).
    Memory Usage: 13.9 MB, less than 48.36% of C++ online submissions for Sqrt(x).