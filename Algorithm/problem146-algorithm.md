# 146. LRU Cache
    Design and implement a data structure for Least Recently Used (LRU) cache. It should support the following operations: get and put.

    get(key) - Get the value (will always be positive) of the key if the key exists in the cache, otherwise return -1.
    put(key, value) - Set or insert the value if the key is not already present. When the cache reached its capacity, it should invalidate the least recently used item before inserting a new item.

    Follow up:
    Could you do both operations in O(1) time complexity?

**Example:**

    Example :
    LRUCache cache = new LRUCache( 2 /* capacity */ );
    cache.put(1, 1);
    cache.put(2, 2);
    cache.get(1);       // returns 1
    cache.put(3, 3);    // evicts key 2
    cache.get(2);       // returns -1 (not found)
    cache.put(4, 4);    // evicts key 1
    cache.get(1);       // returns -1 (not found)
    cache.get(3);       // returns 3
    cache.get(4);       // returns 4

**Code:**
``` C
    class LRUCache {
        list<int> mylist;
        unordered_map<int,int> mymap;
        int length;
    public:
        LRUCache(int capacity) {
            length = capacity;
        }
        
        void put(int key, int value) {
            if(mymap.count(key) < 1){
                if(mylist.size() == length){
                    mymap.erase(*(mylist.begin()));
                    mylist.erase(mylist.begin());
                }	
            }else{
                for(auto it = mylist.begin(); it != mylist.end(); it++){
                    if(*it == key){
                        mylist.erase(it);
                        break;
                    }
                }
            }
            mylist.push_back(key);
            mymap[key] = value;
        }
        
        int get(int key) {
            if(mymap.count(key) > 0){
                put(key,mymap[key]);
                return mymap[key];
            }
            return -1;
        }
        
    };

    /**
    * Your LRUCache object will be instantiated and called as such:
    * LRUCache* obj = new LRUCache(capacity);
    * int param_1 = obj->get(key);
    * obj->put(key,value);
    */
```

**Submission Detail**

    Runtime: 240 ms, faster than 8.05% of C++ online submissions for LRU Cache.
    Memory Usage: 40 MB, less than 45.11% of C++ online submissions for LRU Cache.