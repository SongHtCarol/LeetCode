# 432. All O`one Data Structure
    Implement a data structure supporting the following operations:

    Inc(Key) - Inserts a new key with value 1. Or increments an existing key by 1. Key is guaranteed to be a non-empty string.
    Dec(Key) - If Key's value is 1, remove it from the data structure. Otherwise decrements an existing key by 1. If the key does not exist, this function does nothing. Key is guaranteed to be a non-empty string.
    GetMaxKey() - Returns one of the keys with maximal value. If no element exists, return an empty string "".
    GetMinKey() - Returns one of the keys with minimal value. If no element exists, return an empty string "".
    Challenge: Perform all these in O(1) time complexity.

**Code:**
``` C
    class AllOne {
        unordered_map<string,int> m;
        string min_key, max_key;
    public:
        /** Initialize your data structure here. */
        AllOne() {
            min_key = "";
            max_key = "";
        }
        
        /** Inserts a new key <Key> with value 1. Or increments an existing key by 1. */
        void inc(string key) {
            if(m.count(key) == 0){
                m[key] = 1;
            }else m[key]++;
        }
        
        /** Decrements an existing key by 1. If Key's value is 1, remove it from the data structure. */
        void dec(string key) {
            if(m.count(key) == 0) return ;
            if(m[key] == 1){
                m.erase(key);
            }else{
                m[key]--;
            }
            
        }
        
        /** Returns one of the keys with maximal value. */
        string getMaxKey() {
            if(m.size() == 0) return "";
            if(m.size() == 1){
                max_key = m.begin()->first;
            }else{
                for(auto it = m.begin(); it != m.end(); it++){
                    if(it == m.begin()){
                        max_key = it->first;
                    }else{
                        if(m[max_key] < it->second){
                            max_key = it->first;
                        }
                    }
                }
            }
            return max_key;
        }
        
        /** Returns one of the keys with Minimal value. */
        string getMinKey() {
            if(m.size() == 0) return "";
            if(m.size() == 1){
                min_key = m.begin()->first;
            }else{
                for(auto it = m.begin(); it != m.end(); it++){
                    if(it == m.begin()){
                        min_key = it->first;
                    }else{
                        if(m[min_key] > it->second){
                            min_key = it->first;
                        }
                    }
                }
            }
            return min_key;
        }
    };

    /**
    * Your AllOne object will be instantiated and called as such:
    * AllOne obj = new AllOne();
    * obj.inc(key);
    * obj.dec(key);
    * string param_3 = obj.getMaxKey();
    * string param_4 = obj.getMinKey();
    */
```

**Submission Detail**

    Runtime: 60 ms, faster than 95.67% of C++ online submissions for All O`one Data Structure.
    Memory Usage: 22.2 MB, less than 100.00% of C++ online submissions for All O`one Data Structure.