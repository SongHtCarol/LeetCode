# 42. Trapping Rain Water
    Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.
![rainwatertrap](graph/rainwatertrap.png)
    The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. Thanks Marcos for contributing this image!
**Example:**

    Example :
    Input: [0,1,0,2,1,0,1,3,2,1,2,1]
    Output: 6

**Code:**
``` C
    class Solution {
    public:
        int trap(vector<int>& height) {
            int l = 0, r = height.size()-1;
            if(height.size() < 2) return 0;
            int maxleft = height[l], maxright = height[r], sum = 0;
            while(l < r){
                maxleft  = max(maxleft,height[l]);
                maxright = max(maxright,height[r]);
                if(maxleft <= maxright){
                    sum += (maxleft - height[l]);
                    l++;
                }
                else{
                    sum += (maxright - height[r]);
                    r--;
                }
                //printf("maxleft = %d, maxright = %d, sum = %d \n",maxleft,maxright,sum);
            }
            return sum;
        }
    };
```

**Submission Detail**

    Runtime: 20 ms, faster than 13.97% of C++ online submissions for Trapping Rain Water.
    Memory Usage: 10.9 MB, less than 48.62% of C++ online submissions for Trapping Rain Water.