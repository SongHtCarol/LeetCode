# 192. Word Frequency
    Write a bash script to calculate the frequency of each word in a text file words.txt.
    For simplicity sake, you may assume:
    words.txt contains only lowercase characters and space ' ' characters.
    Each word must consist of lowercase characters only.
    Words are separated by one or more whitespace characters.

**Example:**
    Assume that words.txt has the following content:

    the day is sunny the the
    the sunny is is
    Your script should output the following, sorted by descending frequency:

    the 4
    is 3
    sunny 2
    day 1

**Note:**
    Don't worry about handling ties, it is guaranteed that each word's frequency count is unique.
    Could you write it in one-line using Unix pipes?

**Code:**
``` Bash
    awk '{
        for(i=1; i<=NF; ++i) {++s[$i]}
        }END{
        for(i in s) {print i,s[i]}
    }' words.txt | sort -nr -k2

```

**Submission Detail**

    Runtime: 4 ms, faster than 100.00% of Bash online submissions for Word Frequency.
    Memory Usage: 3.3 MB, less than 43.59% of Bash online submissions for Word Frequency.