# 176. Second Highest Salary
    Write a SQL query to get the second highest salary from the Employee table.
    +----+--------+
    | Id | Salary |
    +----+--------+
    | 1  | 100    |
    | 2  | 200    |
    | 3  | 300    |
    +----+--------+
    For example, given the above Employee table, the query should return 200 as the second highest salary. If there is no second highest salary, then the query should return null.
    +---------------------+
    | SecondHighestSalary |
    +---------------------+
    | 200                 |
    +---------------------+

**Code:**
``` MySQL
    # Write your MySQL query statement below
    SELECT 
        IFNULL(
            (SELECT DISTINCT
                Salary
            FROM
                Employee
            ORDER BY Salary DESC
            LIMIT 1 OFFSET 1),null) AS SecondHighestSalary

```

**Submission Detail**

    Runtime: 139 ms, faster than 47.03% of MySQL online submissions for Second Highest Salary.
    Memory Usage: N/A