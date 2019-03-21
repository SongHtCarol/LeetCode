# 2. Add Two Numbers
    You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

    You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

    Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
    Output: 7 -> 0 -> 8
    Explanation: 342 + 465 = 807.

**Code:**
``` C
    class Solution {
    public:
        ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
            int flag = 0;
            ListNode *tmp1 = l1, *tmp2 = l2;
            ListNode *res = new ListNode(flag);
            ListNode *cur = res;
            while(tmp1 != NULL || tmp2 != NULL){
                ListNode *temp = new ListNode(flag);
                if(tmp1 != NULL) temp->val += tmp1->val;
                if(tmp2 != NULL) temp->val += tmp2->val;
                if(temp->val >= 10){
                    temp->val -= 10;
                    flag = 1;
                }else{
                    flag = 0;
                }

                cur->next = temp;
                cur = cur->next;
                if(tmp1 != NULL)tmp1 = tmp1->next;
                if(tmp2 != NULL)tmp2 = tmp2->next;
            }
            if(flag == 1) {
                ListNode *temp = new ListNode(flag);
                cur->next = temp;
            }
            return res->next;
        }
    };
```

**Submission Detail**

    Runtime: 40 ms, faster than 95.97% of C++ online submissions for Add Two Numbers.
    Memory Usage: 18.9 MB, less than 89.40% of C++ online submissions for Add Two Numbers.