# 71. Simplify Path
    Given an absolute path for a file (Unix-style), simplify it. Or in other words, convert it to the canonical path.

    In a UNIX-style file system, a period . refers to the current directory. Furthermore, a double period .. moves the directory up a level. For more information, see: Absolute path vs relative path in Linux/Unix

    Note that the returned canonical path must always begin with a slash /, and there must be only a single slash / between two directory names. The last directory name (if it exists) must not end with a trailing /. Also, the canonical path must be the shortest string representing the absolute path.

**Example:**

    Example 1:
    Input: "/home/"
    Output: "/home"
    Explanation: Note that there is no trailing slash after the last directory name.

    Example 2:
    Input: "/../"
    Output: "/"
    Explanation: Going one level up from the root directory is a no-op, as the root level is the highest level you can go.

    Example 3:
    Input: "/home//foo/"
    Output: "/home/foo"
    Explanation: In the canonical path, multiple consecutive slashes are replaced by a single one.

    Example 4:
    Input: "/a/./b/../../c/"
    Output: "/c"

    Example 5:
    Input: "/a/../../b/../c//.//"
    Output: "/c"

    Example 6:
    Input: "/a//b////c/d//././/.."
    Output: "/a/b/c"

**Code:**
``` C
    class Solution {
    public:
        string simplifyPath(string path) {
            stack<string> s;
            int i = 0, len = path.length();
            while(i < len){
                while(i < len && path[i] == '/') i++;
                string temp = "";
                while(i < len && path[i] != '/') temp += path[i++];
                if(temp == ".." && !s.empty()) s.pop();
                if(temp != ".." && temp != "" && temp !=".") s.push(temp);
            }
            if(s.size() == 0) return "/";
            string res = "";
            while(!s.empty()){
                res = '/' + s.top() + res;
                s.pop();
            }
            return res;
        }
    };
```

**Submission Detail**

    Runtime: 16 ms, faster than 46.75% of C++ online submissions for Simplify Path.
    Memory Usage: 12.6 MB, less than 32.71% of C++ online submissions for Simplify Path.