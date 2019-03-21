# 1. Two Sum
    Given an array of integers, return indices of the two numbers such that they add up to a specific target.
    You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example:**

    Given nums = [2, 7, 11, 15], target = 9,
    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].

**Code:**
``` C
    class Solution {
    public:
    struct node{
        int value,id;
    };
    vector<node> v;
    static bool cmp1(node a, node b){ return a.value < b.value;}
    vector<int> twoSum(vector<int>& nums, int target) {
        for(int i = 0; i < nums.size(); i++){
            v.push_back({nums[i],i});
        }
        sort(v.begin(),v.end(),cmp1);
        int i = 0, j = v.size() - 1;
        vector<int> temp;
        while(i < j){
            if(v[i].value + v[j].value == target) {
                temp.push_back(v[i].id);
                temp.push_back(v[j].id);
                break;
            }else if(v[i].value + v[j].value < target){
                i++;
            }else{
                j--;
            }
        }
        return temp;
    }
    };
```

**Submission Detail**

    29 / 29 test cases passed.
    Status: Accepted
    Runtime: 12 ms
    Memory Usage: 10 MB
