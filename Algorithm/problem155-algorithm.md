# 155. Min Stack
    Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

    push(x) -- Push element x onto stack.
    pop() -- Removes the element on top of the stack.
    top() -- Get the top element.
    getMin() -- Retrieve the minimum element in the stack.

**Example:**

    Example :
    MinStack minStack = new MinStack();
    minStack.push(-2);
    minStack.push(0);
    minStack.push(-3);
    minStack.getMin();   --> Returns -3.
    minStack.pop();
    minStack.top();      --> Returns 0.
    minStack.getMin();   --> Returns -2.

**Code:**
``` C
    class MinStack {
	int min;
    int _top = -1;
    int val[1000] = {0};
public:
    /** initialize your data structure here. */
    
    MinStack() {
    }
    
    void push(int x) {
    	if(_top == 999) return ;
    	if(_top == -1) min = x;
    	else if(min > x) min = x;
        val[++_top] = x;
    }
    
    void pop() {
    	if(_top == -1) return ;
    	if(val[_top] == min && _top != 0){
    		min = val[0];
    		for(int i = 1; i < _top; i++){
    			if(min > val[i]) min = val[i];
			}
		}
        _top--;
    }
    
    int top() {
    	if(_top == -1) return -1;
        return val[_top];
    }
    
    int getMin() {
    	if(_top == -1) return -1;
        return min;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */

```

**Submission Detail**

    Runtime: 32 ms, faster than 99.20% of C++ online submissions for Min Stack.
    Memory Usage: 17 MB, less than 52.15% of C++ online submissions for Min Stack.