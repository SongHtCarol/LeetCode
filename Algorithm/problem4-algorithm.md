# 4. Median of Two Sorted Arrays
    There are two sorted arrays nums1 and nums2 of size m and n respectively.
    Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

    You may assume nums1 and nums2 cannot be both empty.

**Example:**

    Example 1:
    nums1 = [1, 3]
    nums2 = [2]
    The median is 2.0

    Example 2:
    nums1 = [1, 2]
    nums2 = [3, 4]
    The median is (2 + 3)/2 = 2.5

**Code:**
``` C
    class Solution {
    public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int n = nums1.size(), m = nums2.size();
        if(n > m){
            vector<int> temp = nums1; nums1 = nums2; nums2 = temp;
            swap(n,m);
        }
        int iMin = 0, iMax = n , half = (m+n+1)/2;
        
        while(iMin <= iMax){
            int i = (iMin+iMax)/2, j = half - i;
            if(i < iMax && nums1[i] < nums2[j-1]){
                iMin = i + 1;
            }
            else if(i > iMin && nums1[i-1] > nums2[j]){
                iMax = i-1;
            }
            else{
                double mid = 0;
                if(i == 0) mid = nums2[j-1];
                else if(j == 0) mid = nums1[i-1];
                else mid = nums1[i-1] > nums2[j-1] ? nums1[i-1] : nums2[j-1];
                if((m+n)%2 == 1) return mid;
                
                if(i == n) mid += nums2[j];
                else if(j == m) mid += nums1[i];
                else mid += nums1[i] < nums2[j] ? nums1[i] : nums2[j];
                return mid/2.0;
            }
        }
        return 0.0;
    }
    };
```

**Submission Detail**

    Runtime: 40 ms, faster than 97.34% of C++ online submissions for Median of Two Sorted Arrays.
    Memory Usage: 21.5 MB, less than 47.35% of C++ online submissions for Median of Two Sorted Arrays.